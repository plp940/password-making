# password-making
import java.util.*;
public class passwordgenerator {
    private static final String CHARACTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"+
        "abcdefghijklmnopqrstuvwxyz" + "0123456789" +"!@#$%^&*"   ;
 public static void main(String []args){

    Scanner sc = new Scanner(System.in);
      
    System.out.println("do you want to get suggest strong password[no][yes]");
    String choice = sc.nextLine();



    if (choice.equalsIgnoreCase("yes")) {

      // System.out.print("Enter the length of the password: ");
      // int length = sc.nextInt();
       int length = 15;
       String password = generatePassword(length);
       boolean isStrong = checkPasswordStrength(password);
        System.out.println("Your generated password is: " + password);
        if (isStrong) {
            System.out.println("Your password is strong!");
        } else {
            System.out.println("Your password is weak. Please consider changing it.");
        }
    } 
    
    else if ( choice.equalsIgnoreCase("no")) 
    {System.out.print("Enter your own password: ");
    String password = sc.nextLine();     System.out.println("Your password is: " + password);
  /*   checkPasswordStrength(password); 
    {
        System.out.println(isStrong);
    } 
   
*/

boolean isStrong = checkPasswordStrength(password); // Define the isStrong variable here
if (isStrong) {
    System.out.println("Your password is strong!");
} else {
    System.out.println("Your password is weak. Please consider changing it.");
}



}




    else {  System.out.println("Invalid choice. Please enter Yes or No."); }

   sc.close();

}
private static String generatePassword(int length) {
    Random random = new Random();
    StringBuilder sb = new StringBuilder(length);            //string builder is a class in java which has methods append,insert,replace,delete
    for (int i = 0; i < length; i++) {
        int index = random.nextInt(CHARACTERS.length());
        char randomChar = CHARACTERS.charAt(index);
        sb.append(randomChar);
    }
    return sb.toString();
 }    
 public static boolean checkPasswordStrength(String password) {
    // Check password strength here and return true if it is strong, false otherwise
    int length = password.length();
    boolean hasUppercase = false;
    boolean hasLowercase = false;
    boolean hasDigit = false;
    boolean hasSpecialChar = false;
    
    for (int i = 0; i < length; i++) {
        char ch = password.charAt(i);
        
        if (Character.isUpperCase(ch)) {
            hasUppercase = true;
        } else if (Character.isLowerCase(ch)) {
            hasLowercase = true;
        } else if (Character.isDigit(ch)) {
            hasDigit = true;
        } else if (CHARACTERS.indexOf(ch) != -1) {
            hasSpecialChar = true;
        }
    }
    
    boolean isStrong= (length >= 8 && hasUppercase && hasLowercase && hasDigit && hasSpecialChar);
    return isStrong;
}
}
