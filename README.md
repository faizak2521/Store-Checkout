
```c
#include <stdio.h>

// Function prototypes
float calculateDiscount(float purchaseAmount, float discountRate);
float calculateDiscountedAmount(float purchaseAmount, float discountAmount);
float calculateTax(float purchaseAmount);
float calculateTotalPurchase(float purchaseAmount, float taxAmount);

int main() {
    float purchaseAmount = 0; // Represents the user's purchase amount.
    float discountRate; // Discount rate based on purchase amount.
    char spiritWear; // Indicates whether spirit wear is included.

    printf("Enter the purchase amount: ");
    scanf("%f", &purchaseAmount);
    fflush(stdin);
    printf("Does your purchase include Spirit Wear? (Y/N): ");
    scanf(" %c", &spiritWear);
    fflush(stdin);

    // Apply discount based on purchase amount.
    discountRate = (purchaseAmount >= 100) ? 0.09f : 0.06f;

    if (spiritWear == 'Y' || spiritWear == 'y') {
        // Calculate discount amount.
        float discountAmount = calculateDiscount(purchaseAmount, discountRate);
        // Calculate discounted purchase amount.
        float discountedAmount = calculateDiscountedAmount(purchaseAmount, discountAmount);
        // Calculate tax amount.
        float taxAmount = 0.04f * discountedAmount;
        // Calculate total purchase amount with discount and tax.
        float totalPurchase = discountedAmount + taxAmount;

        // Display receipt details.
        printf("\nPurchase Amount: $%.2f\n", purchaseAmount);
        printf("Discount (%d%%): $%.2f\n", (int)(discountRate * 100), discountAmount);
        printf("Purchase Amount After Discount: $%.2f\n", discountedAmount);
        printf("Sales Tax (4%%): $%.2f\n", taxAmount);
        printf("Total Purchase: $%.2f\n", totalPurchase);
    } else if (spiritWear == 'N' || spiritWear == 'n') {
        // Calculate tax amount without discount.
        float taxAmount = calculateTax(purchaseAmount);
        // Calculate total purchase amount without discount.
        float totalPurchase = calculateTotalPurchase(purchaseAmount, taxAmount);

        // Display receipt details.
        printf("\nPurchase Amount: $%.2f\n", purchaseAmount);
        printf("Sales Tax (4%%): $%.2f\n", taxAmount);
        printf("Total Purchase: $%.2f\n", totalPurchase);
    } else {
        printf("Invalid input. Please enter Y or N.\n");
    }

    return 0;
}

float calculateDiscount(float purchaseAmount, float discountRate) {
    return purchaseAmount * discountRate;
}

float calculateDiscountedAmount(float purchaseAmount, float discountAmount) {
    return purchaseAmount - discountAmount;
}

float calculateTax(float purchaseAmount) {
    return purchaseAmount * 0.04f;
}

float calculateTotalPurchase(float purchaseAmount, float taxAmount) {
    return purchaseAmount + taxAmount;
}
```
