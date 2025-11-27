# Currency-Converter
    #include <stdio.h>

    struct Currency {
    char name[4];
    float rate;
    };

    int main() {
    struct Currency currencies[5] = {
        {"USD", 1.0},
        {"INR", 83.0},
        {"EUR", 0.93},
        {"GBP", 0.82},
        {"JPY", 142.0}
    };
    
    int choice1, choice2;
    float amount, converted;

    printf("Welcome to Currency Converter! \n");
    for(int i = 0; i < 5; i++)
        printf("%d. %s\n", i+1, currencies[i].name);

    printf("Source currency number: "); 
    scanf("%d", &choice1);
    if(choice1 < 1 || choice1 > 5) {
        printf("Invalid choice!\n"); 
        return 0;
    }

    printf("Target currency number: "); 
    scanf("%d", &choice2);
    if(choice2 < 1 || choice2 > 5) {
        printf("Invalid choice!\n"); 
        return 0;
    }

    printf("Amount in %s: ", currencies[choice1-1].name);
    scanf("%f", &amount);
    if(amount < 0) { 
        printf("Amount cannot be negative!\n"); 
        return 0;
    }

    converted = amount * (currencies[choice2-1].rate / currencies[choice1-1].rate);
    printf("\n%.2f %s = %.2f %s \n", 
           amount, currencies[choice1-1].name, 
           converted, currencies[choice2-1].name);

    return 0;
    }
