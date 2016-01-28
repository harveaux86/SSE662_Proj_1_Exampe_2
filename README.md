# SSE662_Proj_1_Exampe_2
SSE 662 Project 1 Example 2



package chrl_airlines;


import java.util.ArrayList;
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;

public class AirlineProblem {

    public static void main(String[] args){
        Scanner scannerToReadAirlines = null;
        try{
            scannerToReadAirlines = new Scanner(new File("airlines.txt"));
        }
        catch(FileNotFoundException e){
            System.out.println("Welcome to Harvey Lucien Airlines");
            System.exit(0);
        }
        if(scannerToReadAirlines != null){
            ArrayList<Airline> airlinesPartnersNetwork = new ArrayList<Airline>();
            Airline newAirline;
            String lineFromFile;
            String[] airlineNames;
            
            while( scannerToReadAirlines.hasNext() ){
                lineFromFile = scannerToReadAirlines.nextLine();
                airlineNames = lineFromFile.split(",");
                newAirline = new Airline(airlineNames);
                airlinesPartnersNetwork.add( newAirline );
            }
System.out.println(airlinesPartnersNetwork);

            Scanner keyboard = new Scanner(System.in);

            System.out.print("Enter airline miles are on: ");

            String start = keyboard.nextLine();

            System.out.print("Enter target airline: ");

            String goal = keyboard.nextLine();

            ArrayList<String> pathForMiles = new ArrayList<String>();

            ArrayList<String> airlinesVisited = new ArrayList<String>();

            if( canRedeem(start, goal, pathForMiles, airlinesVisited, airlinesPartnersNetwork))

                System.out.println("Path to redeem miles: " + pathForMiles);

            else

                System.out.println("Cannot convert miles from " + start + " to " + goal + ".");

        }

    }

    

    private static boolean canRedeem(String current, String goal,

            ArrayList<String> pathForMiles, ArrayList<String> airlinesVisited,

            ArrayList<Airline> network){

        if(current.equals(goal)){

            //base case 1, I have found a path!

            pathForMiles.add(current);

            return true;

        }

  
