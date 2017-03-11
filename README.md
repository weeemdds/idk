#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<time.h>


void menu();
void check_in();
void edit_guest();
void food_menu();
void search_guest();
void check_out();



struct contact_information //start of struct
{
	char firstname[10];
	char lastname[10];
	char address[20];
	char city[20];
	char country[20];
	char nationality[20];
	char gender;
	char email[20];
	int phonenumber;
    int age;
	int guest_id;
	int day, day1;
	int month, month1;
	int year, year1;
}; //end of struct

struct contact_information guests[20];
int s;
int sel;
int product1, product2,product3,product4;
int num;
int again;
int total;
int amount;
int choice;
int servings;
int i = 0;
int rem = 1;
int modify = 1;
int size=sizeof(s);
char lastname[20];
bool w; // controls while loop
			
FILE *f;
	
int main(){ //main function

	int i = 0;
	int temp;
	int id;
	int r;
	char name[20];
	char password[10];
    w = true;
	
	
    
	for(r=1; r<=3; r++){
		
		system("color 03");//change the colour of words and background
        system("cls");//clears the screen
        printf("%s\n",__TIME__);//tells the time
        printf("%s",__DATE__);//tells the date
        printf("\n\t\t\t* * * * * * * * * * * * * * * *\n");
        printf("\n\t#################################################################");
       printf("\n\n\n\t@\t\t\t- -  WELCOME TO - -\t\t\t@");
       printf("\n\n\n\t@\t\t\t-- THE ASHIAH HOTEL --\t\t\t@");
       printf("\n\n\n\t@\t\t     - - MANAGEMENT SYSTEM - -       \t\t@");
       printf("\n\n\n\t@\t\t       DONE BY: WHITNEY FEARON\t\t\t@");
        printf("\n\n\n\t#################################################################\n");
		printf("\n\t\t\t* * * * * * * * * * * * * * * *");
		printf("\n\n\t\tEnter Username: ");
		scanf("%s",name);
		printf("\n\n\n\n\t\tEnter Employee Id: ");
		scanf("%i", &id);
		printf("\n\n\n\n\t\tEnter Password: ");
 
     for (i=0; i<5; ) //a loop to protect password privacy
			{
				temp = getch();
				if (temp=='\b')
				{
					printf ("\n");
					if (i>0)
						i--;
				}
				else
				{
					printf ("*"); // as the password is typed it is replaced by an '*'
					password[i] = temp;
					i++;
				}
			password[i] = '\0'; 
			} //end of loop
			                 

	if (strcmp(name,"User")==0  && strcmp(password, "Hello")==0){ //strcmp: compares two strings and return 0 if both are identical
	printf("\n\n\n\n\t\t = = ACCESS GRANTED = = \n\n\n\n"); // if password is correct
	system("PAUSE");//allows the user to see what is on the screen before the screen is cleared
	system("CLS");// clears the screen
	menu(); //continues the program
	break;
} else { // if password is incorrect
    printf("\n\n\n\n\n\t\tThe Entry Entered Is Invalid.\n");
	printf("\n\n\n\n\n\t\tYou have %i attempts remaining", 3-r); // calculates how much attempts are left
	getch();
	system("CLS");
		printf("\n\t\t\tYou have no more tries!\n\n");
		} // end of else
	} // end of for loop
	
	printf("\n\t\t\tGOODBYE.\n\n\n\n");
}// end of main function

                      
//**************************************************************************************   
     
	            
void menu(){ // start of option function
	
		while(w){ // whenever w is true the loop continues
		system("color fc");	
		printf("%s\n",__TIME__);//tells the time
        printf("%s",__DATE__);//tells the date
		printf("\n\n - - \2 WELCOME TO THE ASHIAH HOTEL \2 - -\n\t\t\t"); 
		printf("\n\n\t\t\t************************************");
		printf("\n\t\t\t\t = = MAIN MENU = = \n");
		printf("\t\t\t************************************");
		printf("\n\n1. Check In");
		printf("\n\n2. Edit and Update");
		printf("\n\n3. Make Food Orders");
		printf("\n\n4. Search Guest");
		printf("\n\n5. Check Out");
		printf("\n\n6. EXIT");
		printf("\n\n\t\t\tEnter Your Choice:");
		scanf("%i", &sel); // user inputs
        
        if (sel == 1){ // beginning of loop
        	
         	system("CLS");
         	printf("\n* * * * * * GUEST'S INFORMATION * * * * * *\n\n");
         	check_in();		// if 1 is entered go to check_in function
		    printf("\n\nPress any key to get back to the menu ");
		    getch();
		    system("CLS");
		 } else if (sel == 2){
		 	
     	   system("CLS");
     	   printf("\n* * * * * * EDIT GUEST'S INFORMATION * * * * * *\n\n");
     	   edit_guest(); // if 2 is entered go to edit_guest function
		   printf("\n\nPress any key to get back to the menu ");
		   getch();
		   system("CLS");
		   
		   
	} else if (sel == 3){
		
		system("CLS");
		printf("\n\t\t\t    Ashiah Hotel Food Menu  \n\n ");
        printf("\t\t\t+============================+\n\n");
		food_menu(); // if 3 is entered go to food_menu function
		printf("\n\nPress any key to get back to the menu ");
		getch();
		system("CLS");
		
		
   
   } else if (sel == 4){
   	
    	system("CLS");
    	printf("\n* * * * * * SEARCH FOR A GUEST * * * * * *\n\n");
    	search_guest(); // if 5 is entered go to search_guest function
    	printf("\n\n Press any key to get back to the menu ");
		getch();
		system("CLS");
		
  } else if (sel == 5){
   	
   	system("CLS");
   	printf("\n\t * * * CHECKOUT * * *");
   	check_out(); // if 6 is entered go to check_out function
   	printf("\n\nPress any key to get back to the menu ");
	getch();
	system("CLS");
	
   } else if (sel == 6){
   
   system("CLS");
      printf("\n\n\n\t    ########################################################\n");
      printf("\t    THANK YOU FOR USING THE ASHIAH HOTEL MANAGEMENT SYSTEM");
      printf("\n\t    ########################################################\n");
   w = false; // stops loop
			
    } else{
			
			system("CLS");
			printf("Nothing was selected!");
			printf("\n\nPress any key to get back to the menu ");
			getch();
			system("CLS");	 
		}
	} // end of while loop
} //end of option function
	
	
//**************************************************************************************   


void check_in(){ // start of checkin function

	printf("\n Enter Guest ID:\t");
	scanf("\t%i",&guests[i].guest_id);				
	printf("\n Enter Date of Arrival(dd/mm/yy): \t"); 
	scanf("\t%i/%i/%i",&guests[i].day,&guests[i].month,&guests[i].year); 
	printf("\n Enter First Name: \t");
	scanf("\t%s", guests[i].firstname);
	printf("\n Enter Last Name: \t");
	scanf("\t%s",guests[i].lastname);
	printf("\n Enter Gender (M/F): \t");
	scanf("\t%c", &guests[i].gender);
	printf("\n Enter Age: \t");
	scanf("\t%i", &guests[i].age);
	printf("\n Enter Date Of Birth (dd/mm/yy): \t");
	scanf("\t%i/%i/%i",&guests[i].day1,&guests[i].month1,&guests[i].year1); 
	printf("\n Enter Home Address: \t");
	scanf("\t%s", guests[i].address);
	printf("\n Enter City: \t");
	scanf("\t%s",guests[i].city);
	printf("\n Enter Country: \t");
	scanf("\t%s",guests[i].country);
	printf("\n Enter Nationality: \t");
	scanf("\t%s", guests[i].nationality);
	printf("\n Enter Email: \t");
	scanf("\t%s",guests[i].email);
	printf("\n Enter Phone Number: \t");
	scanf("\t%i", &guests[i].phonenumber);

// a file called hotel records was created to store guests personal information
    f = fopen ("Hotel Records.txt","w");
    
// selection statement used to check if file exists
    if (f == NULL)
    printf("File inaccessible");	
	else{
	     for (s=0; s<1; s++){
            fprintf(f,"\t%i\t%i/%i/%i\t%s\t%s\t%c\t%i\t%i/%i/%i\t%s\t%s\t%s\t%s\t%s\t%i\t\t",guests[i].guest_id, guests[i].day,guests[i].month,guests[i].year,guests[i].firstname,guests[i].lastname,guests[i].gender,guests[i].age,guests[i].day,guests[i].month,guests[i].year,guests[i].address,guests[i].city,guests[i].country,guests[i].nationality,guests[i].email,guests[i].phonenumber);	
	} //endfor
	fclose(f); 
}
} //end of checkin function


//**************************************************************************************   


void edit_guest(){
	

printf("\n\tENTER THE LAST NAME OF GUEST TO BE EDITED:");

scanf("%s", lastname); //locates record of lastname entered

while (!feof(f)){
 
if(strcmp(lastname,guests[i].lastname)==0){ //compares two strings and return 0 if both are identical
 
    printf("\nYOUR OLD RECORD WAS:\n");
    printf("\n Guest's ID: %i", guests[i].guest_id);
    printf("\n Date of Arrival: %i/%i/%i", guests[i].day,guests[i].month,guests[i].year);
 	printf("\n First Name: %s", guests[i].firstname);
 	printf("\n Last Name: %s", guests[i].lastname);
 	printf("\n Gender: %c", guests[i].gender);
	printf ("\n Age: %i", guests[i].age);
 	printf("\n Date of Birth: %i/%i/%i", guests[i].day1,guests[i].month1,guests[i].year1);
 	printf("\n Home Address: %s ", guests[i].address);
 	printf("\n City: %s", guests[i].city);
 	printf("\n Country: %s", guests[i].country);
 	printf("\n Nationality: %s", guests[i].nationality);
 	printf("\n Email: %s", guests[i].email);
	printf("\n Phone Number: %i", guests[i].phonenumber);
    printf("\n\n= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = ");
    // edit menu
    printf("\n\n\t\tWHAT WOULD YOU LIKE TO EDIT..\n\n");
    printf("\n1.Date of Arrival.");
    printf("\n2.First Name");
    printf("\n3.Last Name.");
    printf("\n4.Gender");
    printf("\n5.Age");
    printf("\n6.Date of Birth.");
    printf("\n7.Home Address");
    printf("\n8.City");
	printf("\n9.Country");
    printf("\n10.Nationality");
    printf("\n11.Email");
    printf("\n12.Phone Number");
	printf("\n13.WHOLE RECORD.");
    printf("\n14.GO BACK TO MAIN MENU.");
    
    // a file called hotel records was created to store guests personal information
    f = fopen ("Hotel Records.txt","r+");
    
// selection statement used to check if file exists
    if (f == NULL)
    printf("File inaccessible");	
	else{
	     for (s=0; s<1; s++){
             fprintf(f,"\t%i\t%i/%i/%i\t%s\t%s\t%c\t%i\t%i/%i/%i\t%s\t%s\t%s\t%s\t%s\t%i\t\t",guests[i].guest_id, guests[i].day,guests[i].month,guests[i].year,guests[i].firstname,guests[i].lastname,guests[i].gender,guests[i].age,guests[i].day,guests[i].month,guests[i].year,guests[i].address,guests[i].city,guests[i].country,guests[i].nationality,guests[i].email,guests[i].phonenumber);	
	} //endfor
	fclose(f); 
}

    printf("\n\n\n\tENTER YOUR CHOICE: ");
    scanf("%i",&num);
 
    switch(num){
 
    case 1: 
    system("CLS");										
	printf("\n Enter NEW Date of Arrival(dd/mm/yy): \t");										        
	scanf("\t%i/%i/%i",&guests[i].day,&guests[i].month,&guests[i].year); 
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
	edit_guest();										                                     
	system("CLS");
	break;
																									
    case 2: 
    system("CLS");
	printf("\n Modify First Name: \t");
	scanf("\t%s", guests[i].firstname);
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
    
	case 3: 
    system("CLS");
	printf("\n Modify Last Name: \t");
	scanf("\t%s",guests[i].lastname);
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
                                            
    case 4: 
    system("CLS");
	printf("\n Modify Gender (M/F): \t");
 	scanf("\t%c", &guests[i].gender);
    printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;										
	
	case 5: 
	system("CLS");
	printf("\n Modify NEW Age: \t");
 	scanf("\t%i", &guests[i].age);
    printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
	
	case 6: 
	system("CLS");
	printf("\n Enter NEW Date Of Birth (dd/mm/yy): \t");
	scanf("\t%i/%i/%i",&guests[i].day1,&guests[i].month1,&guests[i].year1); 
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
	
  	case 7: 
  	system("CLS");
    printf("\n Enter NEW Home Address: \t");
	scanf("\t%s", guests[i].address);
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
	                                   
    case 8: 
    system("CLS");
	printf("\n Enter NEW City: \t");
	scanf("\t%s",guests[i].city); 
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
										
    case 9: 
    system("CLS");
	printf("\n Enter NEW Country: \t");
	scanf("\t%s",guests[i].country);
    printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
	
	case 10: 
	system("CLS");
	printf("\n Enter NEW Nationality: \t");
	scanf("\t%s", guests[i].nationality);
	printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
											
   case 11: 
   system("CLS");
   printf("\n Enter NEW Email: \t");
   scanf("\t%s",guests[i].email);
   printf("\n\n\t\t :: FILE UPDATED ::");
   printf("\n\n");
   edit_guest();
   system("CLS");
   break;
	
   case 12: 
   system("CLS");
   printf("\n Enter NEW Phone Number: \t");
   scanf("\t%i", &guests[i].phonenumber);										
   printf("\n\n\t\t :: FILE UPDATED ::");
   printf("\n\n");
   edit_guest();
   system("CLS");
   break;	
											
    case 13:  
    system("CLS");
	printf("\n Enter Date of Arrival(dd/mm/yy): \t"); 
	scanf("\t%i/%i/%i",&guests[i].day,&guests[i].month,&guests[i].year); 
	printf("\n Enter First Name: \t");
	scanf("\t%s", guests[i].firstname);
	printf("\n Enter Last Name: \t");
	scanf("\t%s",guests[i].lastname);
	printf("\n Enter Gender (M/F): \t");
	scanf("\t%c", &guests[i].gender);
	printf("\n Enter Age: \t");
	scanf("\t%i", &guests[i].age);
	printf("\n Enter Date Of Birth (dd/mm/yy): \t");
	scanf("\t%i/%i/%i",&guests[i].day1,&guests[i].month1,&guests[i].year1); 
	printf("\n Enter Home Address: \t");
	scanf("\t%s", guests[i].address);
	printf("\n Enter City: \t");
	scanf("\t%s",guests[i].city);
	printf("\n Enter Country: \t");
	scanf("\t%s",guests[i].country);
	printf("\n Enter Nationality: \t");
	scanf("\t%s", guests[i].nationality);
	printf("\n Enter Email: \t");
	scanf("\t%s",guests[i].email);
	printf("\n Enter Phone Number: \t");
	scanf("\t%i", &guests[i].phonenumber);
    printf("\n\n\t\t :: FILE UPDATED ::");
	printf("\n\n");
    edit_guest();
    system("CLS");
	break;
	                                       
	case 14: 
	printf("\nPRESS ANY KEY TO GO BACK...\n");
    getch();
    system("CLS");
	menu();
    break;
                                                    
    default: 
    printf("\nYOU TYPED SOMETHING ELSE...TRY AGAIN\n");
    break;
    modify=0;
                                                     
} // end of switch
    while (i++);                                    
} // end of if statement
 
            else{
	
	        printf("\t\n :: Guest Not Found ::");
	
	        printf("\n\n Would you like to search again?\n 1. Yes , 2. No : ");
	
			scanf("%i", &again);
			
			system("CLS");
		
			 if (again == 1 ){
			 	
			 edit_guest();
			 
			} else if (again == 2 ){
				 	
				 menu();	 
			}
		} // end of else
	} //end of while
		
}//end of update function


//**************************************************************************************   


void food_menu(){ 
	
        system("CLS");
        printf("\n\t\t================================\n\t\t\t MENU ITEMS\n\t\t================================");
		printf("\n\n::::::::::::::::::::::::::::::::::::::::::::::::::::::::");
		printf("\n\n\t1. Ackee and Saltfish with Ground Provisions  = $1500");
		printf("\n\n\t2. Cheese Patty = $150");
		printf("\n\n\t3. Jamaican Jerk Chicken = $1000");
		printf("\n\n\t4. Island Fruit Juice = $400");
		printf("\n\n\t5. Account Balance \3");
		printf("\n\n\t6. Return To Main Menu \2");
		printf("\n\n::::::::::::::::::::::::::::::::::::::::::::::::::::::::::\n\n");
		
		printf("Enter Choice");
		scanf("%i", &choice);
		
		while (w){
			
		if (choice==1){
			
			printf("\n\nEnter Number of Servings");
            scanf("%i", &servings);
            product1 = (servings * 1500);
            printf ("\n\nYour total amount is %i", product1);
            printf("\nWould you like to buy anything else?\n [1] Yes , [2] No : ");
			scanf("%i", &again);
			system("cls");
		
			 if (again == 1 ){
			 	
			 food_menu();
			 
			 } else 
				if (again == 2 ){
				menu();
				}
				 
		} else if (choice==2){
			
			printf("\n\nEnter Number of Servings");
            scanf("%i", &servings);
            product2 = (servings * 150);
            printf ("\n\nYour total amount is %i", product2);
            printf("\nWould you like to buy anything else?\n [1] Yes , [2] No : ");
			scanf("%i", &again);
			system("cls");
		
			if (again == 1 ){
			food_menu();
			 } else 
				if (again == 2 ){
			    menu();
				}
			}
				 
			else if (choice==3){
			
			printf("\n\nEnter Number of Servings");
            scanf("%i", &servings);
            product3 = (servings * 1000);
            printf ("\n\nYour total amount is %i", product3);
            printf("\nWould you like to buy anything else?\n [1] Yes , [2] No : ");
			scanf("%i", &again);
			system("cls");
		
			if (again == 1 ){
			food_menu();
			 } else 
				if (again == 2 ){
				menu();	 
		    }
		}
		else if (choice==4){
			
			printf("\n\nEnter Number of Servings");
            scanf("%i", &servings);
            product4 = (servings * 400);
            printf ("\n\nYour total amount is %i", product4);
            printf("\nWould you like to buy anything else?\n [1] Yes , [2] No : ");
			scanf("%i", &again);
			system("cls");
		
			if (again == 1 ){
			food_menu();
			 } else 
				if (again == 2 ){
				menu();
	        }
	    }
 else if (choice==5){
			
	total = (product1+product2+product3+product4);
	printf ("\nYour balance is %i", total);
break;
   }
else if (choice==6){
		
    system("CLS");
	menu();
	w=false;
		
	}
	
else{
	printf("Nothing was selected!");
	printf("\n\nPress any key to get back to the menu ");
	getch();
	system("CLS");
	break;
	}
   }
} // end of foodmenu function


//**************************************************************************************   


void search_guest(){ 

printf("\t\n Enter Last Name of Guest:");

scanf("%s",lastname);

while (1){ 

if (strcmp(lastname,guests[i].lastname)==0){
	
	system("CLS");
    printf(" \n\t * * RECORD FOUND * *\n\n");
	printf("\n Guest's ID: %i", guests[i].guest_id);
 	printf("\n Date of Arrival: %i/%i/%i", guests[i].day,guests[i].month,guests[i].year);
 	printf("\n First Name: %s", guests[i].firstname);
 	printf("\n Last Name: %s", guests[i].lastname);
 	printf("\n Gender: %c", guests[i].gender);
 	printf ("\n Age: %i", guests[i].age);
 	printf("\n Date of Birth: %i/%i/%i", guests[i].day1,guests[i].month1,guests[i].year1);
 	printf("\n Home Address: %s ", guests[i].address);
 	printf("\n City: %s", guests[i].city);
 	printf("\n Country: %s", guests[i].country);
 	printf("\n Nationality: %s", guests[i].nationality);
 	printf("\n Email: %s", guests[i].email);
	printf("\n Phone Number: %i\n\n", guests[i].phonenumber);
	system("PAUSE");
	system("CLS");
    menu();

}

else if (rem==1){
	
	printf("\t\n = = Guest Not Found");
	
	printf("\n\n Would you like to search again?\n [1] Yes , [2] No : ");
	
			scanf("%i", &again);
			system("CLS");
		
			 if (again == 1 ){
			 	
			 search_guest();
			 
			 } else 
			 
				 if (again == 2 ){
				 	
				 menu();
				 
				 }
	
}

i++;

}
    // a file called hotel records was created to store guests personal information
    f = fopen ("Hotel Records.txt","r");
    
// selection statement used to check if file exists
    if (f == NULL)
    printf("File inaccessible");	
	else{
	     for (s=0; s<1; s++){
             fscanf(f,"\t%i\t%i/%i/%i\t%s\t%s\t%c\t%i\t%i/%i/%i\t%s\t%s\t%s\t%s\t%s\t%i\t\t",guests[i].guest_id, guests[i].day,guests[i].month,guests[i].year,guests[i].firstname,guests[i].lastname,guests[i].gender,guests[i].age,guests[i].day,guests[i].month,guests[i].year,guests[i].address,guests[i].city,guests[i].country,guests[i].nationality,guests[i].email,guests[i].phonenumber);	
	} //endfor
	fclose(f); 
}
	
				
}// end of search function 


//**************************************************************************************   

 


//**************************************************************************************   


void check_out() { // start of checkout function
	
	total=(product1+product2+product3+product4);
	printf ("\n\nYour balance is %i", total);
	printf ("\n\nEnter the amount you want to pay:\t");
	scanf("%i",&amount);
	if (total == amount){
		printf ("\n\t Date of Departure:\t");
		scanf("\t%i/%i/%i",&guests[i].day,&guests[i].month,&guests[i].year);
		printf ("\n\n\n\t\t\t GUEST HAVE CHECKED OUT \n\n\n");
	} else{
		printf("The amount you owe is %i", total);
		
	}
	
// a file called hotel records was created to store guests personal information

f = fopen ("Hotel Records.txt","r+");
    
// selection statement used to check if file exists
    if (f == NULL)
    printf("File inaccessible");	
	else{
	     for (s=0; s<1; s++){
             fprintf(f,"\t%i\t%i/%i/%i\t%s\t%s\t%c\t%i\t%i/%i/%i\t%s\t%s\t%s\t%s\t%s\t%i\t\t",guests[i].guest_id, guests[i].day,guests[i].month,guests[i].year,guests[i].firstname,guests[i].lastname,guests[i].gender,guests[i].age,guests[i].day,guests[i].month,guests[i].year,guests[i].address,guests[i].city,guests[i].country,guests[i].nationality,guests[i].email,guests[i].phonenumber);	
	} //endfor
	fclose(f); 
}
	
} //end of checkout function


