
#include <stdio.h>

// Function prototypes
float discountCalculation(float purchase_amount, float discount);// Function prototypes
// Calculates the updated purchase amount after discount.
float discountedPurchaseAmount(float purchase_amount, float discount_total);
float taxAmount(float purchase_amount); // Calculates the dollar amount of tax to be added.
float totalPurchase(float purchase_amount, float taxAmount); // Calculates the total purchase amount.


// Main function
int main() {
    float purchase_amount = 0; // Represents the user's purchase amount.
    float discount; // Variable for spirit wear discount.
    char spirit_wear; // Indicates whether spirit wear is included.


    printf("Enter the purchase amount: "); // Prompt user for purchase amount.
    scanf("%f", &purchase_amount); // Store user input as float for purchase amount.
    fflush(stdin); // Flush to avoid reading unintended characters.
    printf("Does your purchase include Spirit Wear? (Y/N): "); // Prompts user for spirit wear purchase.
    scanf("%c", &spirit_wear); // Store input as character for spirit wear.
    fflush(stdin); // Flush to avoid reading unintended characters.


    // Apply discount based on purchase amount.
    if (purchase_amount >= 100) {
        discount = 0.09f; // 9% discount if purchase amount is >= 100.
    } else {
        discount = 0.06f; // 6% discount if purchase amount is < 100.
    }


    // Apply discount if spirit wear is included.
    if (spirit_wear == 'y' || spirit_wear == 'Y') { // Upper case and lower case conversion.
        // Calculate discount total by calling Function #1.
        float discount_total = discountCalculation(purchase_amount, discount);
        // Calculate purchase amount after discount by calling Function #2.
        float discounted_amount = discountedPurchaseAmount(purchase_amount, discount_total);
        // Calculate tax with discount.
        float tax_w_discount = 0.04f * discounted_amount;
        // Calculate total purchase amount with tax and discount.
        float total_after_tax_w_d = discounted_amount + tax_w_discount;

        // Displays receipt details.
        printf("\nPurchase Amount: $%.2f\n", purchase_amount); // Purchase amount
        printf("Discount (%d%%): $%.2f\n", (int)(discount * 100), discount_total); // Discount amount
        printf("Purchase Amount After Discount: $%.2f\n", discounted_amount); // Purchase amount after discount
        printf("Sales Tax (4%%): $%.2f\n", tax_w_discount); // Sales tax with discount
        printf("Total Purchase: $%.2f\n", total_after_tax_w_d); // Total with discount

        // Apply no discount if spirit wear is not included.
    } else if (spirit_wear == 'n' || spirit_wear == 'N') { // Upper case and lower case conversion.
        // Calculate sales tax without discount by calling Function #3.
        float tax_without_discount = taxAmount(purchase_amount);
        // Calculate total purchase amount with tax but no discount by calling Function #4.
        float total_after_tax_without_d = totalPurchase(purchase_amount, taxAmount(purchase_amount));

        // Display receipt details.
        printf("\nPurchase Amount: $%.2f\n", purchase_amount); // Purchase amount
        printf("Sales Tax (4%%): $%.2f\n", tax_without_discount); // Sales tax without discount
        printf("Total Purchase: $%.2f\n", total_after_tax_without_d); // Total without discount

        // Optional, but this handles invalid answers.
    } else {
        printf("Invalid answer. Please try again with Y or N. "); // Prints invalidation of input
    }
    return 0; // No errors returned
}


// Function 1: Calculates the dollar amount of the discount by calling if spirit wear purchased.
float discountCalculation(float purchase_amount, float discount) {
    // Stores discount amount by multiplying the purchase amount and discount amount.
    float discountAmount = purchase_amount * discount;
    return discountAmount; // Returns the calculated discount amount.
}

// Function 2: Calculates the updated purchase amount after discount by calling if spirit wear purchased.
float discountedPurchaseAmount(float purchase_amount, float discount_total) {
    // Stores total purchase amount after discount by subtracting the discount total from the purchase amount.
    float discountedPurchaseAmount = purchase_amount - discount_total;
    return discountedPurchaseAmount;  // Returns the discounted purchase amount.
}

// Function 3: Calculates the dollar amount of tax that should be added on by calling if spirit wear isn't purchased.
float taxAmount(float purchase_amount) {
    // Stores tax amount by multiplying total purchase amount by 4% tax.
    float taxAmount = purchase_amount * 0.04f;
    return taxAmount; // Returns the calculated tax amount.
}

// Function 4: Calculates the total purchase amount by calling if spirit wear isn't purchased.
float totalPurchase(float purchase_amount, float taxAmount) {
    // Stores total purchase amount by adding purchase amount plus the sales tax.
    float totalPurchase = purchase_amount + taxAmount;
    return totalPurchase; // Returns the total purchase amount.
}
