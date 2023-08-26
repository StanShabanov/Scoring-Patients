import java.util.*;
import java.lang.Math;
public class PatientPrioritizer {
   public static final int HOSPITAL_ZIP = 12345;
   public static void main(String[] args){
      String name = "";
      int patients = 0;
      int highScore = 0;
      
      Scanner scan = new Scanner(System.in); 
      System.out.println("Hello! We value you and your time, so we will help");
      System.out.println("you prioritize which patients to see next!");
      System.out.println("Please answer the following questions about the next patient so");
      System.out.println("we can help you do your best work :)");
      System.out.println();
      
      while(!name.equals("quit")) {
          System.out.println("Please enter the next patient's name or \"quit\" to end the program.");
          System.out.print("Patient's name: ");
          name = scan.next();
          if (name.equals("quit")) {
             break;
          }
    
          System.out.print("Patient age: " );
          int age = scan.nextInt();
          
          System.out.print("Patient zip code: ");
          int zipcode = scan.nextInt();
          while(!fiveDigits(zipcode)) {
             System.out.print("Invalid zip code, enter valid zip code: ");
             zipcode = scan.nextInt();
          }
          
          System.out.print("Is our hospital \"in network\" for the patient's insurance? ");
          String Ins = scan.next();
          boolean network = false;
          if (Ins.equalsIgnoreCase("yes") || Ins.equalsIgnoreCase("y")){
             network = true;
          }
          else{
             network = false;
          }
          
          System.out.print("Patient pain level (1-10): ");
          int pain = scan.nextInt();
          boolean cont = false;
          if (pain >= 1 && pain <=10 ) {
             cont = true;
          }
          while (!cont) {
             System.out.print("Invalid pain level, enter valid pain level (1-10): ");
             pain = scan.nextInt();
             if (pain >= 1 && pain <=10 ) {
                cont = true;
            }
          }
    
          System.out.print("Patient temperature (in degrees Fahrenheit): ");
          double temp = scan.nextDouble();
          System.out.println();
    
          int score = priorityScore(age, zipcode, network, pain, temp);
          if (highScore < score) {
             highScore = score;
          }
          System.out.println("We have found patient " + name + " to have a priority score of: " + score);
          String priority = priority(score);
          
          if (priority == "low priority") {
             System.out.println("We have determined this patient is low priority.");
             System.out.println("Please put them on the waitlist for when a medical provider becomes available.");
          }
          else if (priority == "medium priority"){
             System.out.println("We have determined this patient is medium priority.");
             System.out.println("Please assign an appropriate medical provider to their case");
             System.out.println("and check back in with the patient's condition in a little while.");
          }
          else {
             System.out.println("We have determined this patient is high priority,");
             System.out.println("and it is advised to call an appropriate medical provider ASAP.");
          }
          System.out.println();
    
          System.out.println("Thank you for using our system!");
          System.out.println("We hope we have helped you do your best!");
          System.out.println();
    
          patients ++;
      }

      System.out.println("Statistics for the day:");
      System.out.println("..." + patients + " patients were helped");
      System.out.println("...the highest priority patient we saw had a score of " + highScore);
      System.out.println("Good job today!");
   }


   public static int priorityScore(int age, int zipcode, boolean network, int pain, double temp) {
      int score = 100;
      if (age <= 12 || age >= 75){
         score += 50;
      }
      int firstDigitPatient = Integer.parseInt(Integer.toString(zipcode).substring(0, 1));
      int firstDigitHospital = Integer.parseInt(Integer.toString(HOSPITAL_ZIP).substring(0, 1));
      int secondDigitPatient = Integer.parseInt(Integer.toString(zipcode).substring(1, 2));
      int secondDigitHospital = Integer.parseInt(Integer.toString(HOSPITAL_ZIP).substring(1, 2));
      if (firstDigitPatient == firstDigitHospital) {
         score += 25;
         if (secondDigitPatient == secondDigitHospital) {
         score += 15;
         }
      }
      

      if(network) {
         score += 50;
      }

      pain = pain*10;
      score += pain;
      
      if (temp >= 99.5) {
         score += 8;
      }
      return score;

   }
   public static String priority(int score) {
      String priority;
      if (score >= 332) {
         priority = "high priority";
      }
      else if (score >= 166) {
         priority = "medium priority";
      }
      else {
         priority ="low priority";
      }
      return priority;
   }
   public static boolean fiveDigits(int val) {
      val = val / 10000; // get first digit
      if (val == 0) { // has less than 5 digits
         return false;
      } else if (val / 10 == 0) { // has 5 digits
         return true;
      } else { // has more than 5 digits
         return false; 
      }
      // NOTE: the above can be written with improved "boolean zen" as follows: 
      // return val != 0 && val / 10 == 0;
   }  
}
