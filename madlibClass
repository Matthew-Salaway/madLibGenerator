import java.util.Scanner;
import java.io.File;
import java.util.HashMap;
import java.util.ArrayList;
import java.util.Random;
import java.io.*;
import java.lang.String;
public class ReplaceWord
{
    private static ArrayList<String> nouns = new ArrayList<String>();
    private static ArrayList<String> verbs = new ArrayList<String>();
    private static ArrayList<String> adjectives = new ArrayList<String>();
    private static ArrayList<String> noness = new ArrayList<String>();
    private static final String SPACE = " ";
    static{
        //read in the positive adjectives in postiveAdjectives.txt
        try {
            //PrintWriter out1 = new PrintWriter("91K nouns.txt");
            Scanner input = new Scanner(new File("91K nouns.txt"));
            while(input.hasNextLine()){
                String temp = input.nextLine().trim();
                //System.out.println(temp);
                nouns.add(temp);
            }
            input.close();
        }
        catch(Exception e){
            System.out.println("Error reading or parsing 91k nouns.txt\n" + e);
        }   
        //read in the negative adjectives in negativeAdjectives.txt
        try {
            //PrintWriter out2 = new PrintWriter("31K verbs.txt");
            Scanner input = new Scanner(new File("31K verbs.txt"));
            while(input.hasNextLine()){
                verbs.add(input.nextLine().trim());
            }
            input.close();
        }
        catch(Exception e){
            System.out.println("Error reading or parsing 31k verbs.txt");
        }   
        try {
            //PrintWriter out3 = new PrintWriter("28K adjectives.txt");
            Scanner input = new Scanner(new File("28K adjectives.txt"));
            while(input.hasNextLine()){
                String temp = input.nextLine().trim();
                //System.out.println(temp);
                adjectives.add(temp);
            }
            input.close();
        }
        catch(Exception e){
            System.out.println("Error reading or parsing 28K adjectives.txt" + e);
        }   
        try {
            //PrintWriter out4 = new PrintWriter("6K adverbs.txt");
            Scanner input = new Scanner(new File("nonessentialwords.txt"));
            while(input.hasNextLine()){
                String temp = input.nextLine().trim();
                //System.out.println(temp);
                noness.add(temp);
            }
            input.close();
        }
        catch(Exception e){
            System.out.println("Error reading or parsing noness" + e);
        }   
    }

    public static void main(String[] args){
        // prints out a description of the class and some methods.
        System.out.println("This class is used to generate Mad Libs.");
        System.out.println("Use the method madLibsGenFile if the text you have is stored in a file.");
        System.out.println("And use the method madLibsGenString if the text you have is stored in a String.");
        System.out.println("Try out the method storyTime to try the future of Mibs Libs with interative stories.");

    }

    public static String textToString( String fileName )
    {  
        String temp = "";
        try {
            Scanner input = new Scanner(new File(fileName));
            //add 'words' in the file to the string, separated by a single space
            while(input.hasNext()){
                temp = temp + input.next() + " ";
            }
            input.close();
        }
        catch(Exception e){
            System.out.println("Unable to locate " + fileName);
        }
        //make sure to remove any additional space that may have been added at the end of the string.
        return temp.trim();
    }

    public static String removePunctuation( String word )
    {
        while(word.length() > 0 && !Character.isAlphabetic(word.charAt(0)))
        {
            word = word.substring(1);
        }
        while(word.length() > 0 && !Character.isAlphabetic(word.charAt(word.length()-1)))
        {
            word = word.substring(0, word.length()-1);
        }
        return word;
    }

    public static boolean isEssential(String b){
        String word = b.toLowerCase();
        for(int g = 0; g < noness.size(); g++){  
            if(word.equals(noness.get(g)) || word.equals(" ") || word.equals("")){
                return false;
            }
        }
        return true;
    }

    public static boolean replaceornot() {
        int number = (int) (Math.random()*3 + 420) ;
        if(number == 420){
            return true;
        }
        return false;
    }

    public static String ReplaceWordBetter(String w)
    {
        String wordOg = w;
        String word = removePunctuation(wordOg.toLowerCase());
        boolean adj = false;
        boolean verb = false;
        boolean noun = false;
        boolean adverb = false;
        if(isEssential(word)){
            for(int i = 0; i < verbs.size(); i++){
                if(word.equals(verbs.get(i))){
                    verb = true;
                }
            }
            for(int i = 0; i < adjectives.size(); i++){
                if(word.equals(adjectives.get(i))){
                    adj = true;
                }
            }
            for(int i = 0; i < nouns.size(); i++){
                if(word.equals(nouns.get(i))){
                    noun = true;
                }
            }
            if(verb && !noun && !adj){
                return "____VERB";
            }
            if(verb && noun && !adj){
                if(replaceornot()){
                    return "____VERB";
                }
            }
            if(!verb && noun && !adj){
                if(replaceornot()){
                    return "____NOUN";
                }
            }
            if(!verb && !noun && adj){
                return "____ADJ";
            }
            if(!verb && noun && adj){
                if(replaceornot()){
                    return "____ADJ";
                }
            }
        }
        return wordOg;
    }

    public static String ReplaceWord(String w)
    {
        String word = w;
        if(isEssential(word)){
            for(int i = 0; i < verbs.size(); i++){
                if(word.equals(verbs.get(i))){
                    if(replaceornot()){
                        return "____VERB";
                    }
                }
            }
            for(int i = 0; i < adjectives.size(); i++){
                if(word.equals(adjectives.get(i))){
                    if(replaceornot()){
                        return "____ADJ";
                    }
                }
            }
            for(int i = 0; i < nouns.size(); i++){
                if(word.equals(nouns.get(i))){
                    if(replaceornot()){
                        return "____NOUN";
                    }
                }
            }
        }
        return word ;
    }

    public static String madLibGenFile(String fileName) {
        main(null);
        String madLib = " " + textToString(fileName) + " ";
        int secondspaceindex = 0;
        while(secondspaceindex != -1){
            int firstspaceindex = madLib.indexOf(" ", secondspaceindex);
            secondspaceindex = madLib.indexOf(" ", firstspaceindex + 1);
            if(secondspaceindex != -1 && firstspaceindex != -1){
                String a = madLib.substring(firstspaceindex + 1, secondspaceindex);
                a = ReplaceWordBetter(a);
                madLib = madLib.substring(0, firstspaceindex + 1) + a + madLib.substring(secondspaceindex);
            }
        }
        return madLib;
    }

    public static String madLibGenString(String s) {
        main(null);
        String madLib = " " + s + " ";
        int secondspaceindex = 0;
        while(secondspaceindex != -1){
            int firstspaceindex = madLib.indexOf(" ", secondspaceindex);
            secondspaceindex = madLib.indexOf(" ", firstspaceindex + 1);
            if(secondspaceindex != -1 && firstspaceindex != -1){
                String a = madLib.substring(firstspaceindex + 1, secondspaceindex);
                a = ReplaceWordBetter(a);
                madLib = madLib.substring(0, firstspaceindex + 1) + a + madLib.substring(secondspaceindex);
            }
        }
        return madLib;
    }

    public static void storyTime(){
        main(null);
        Scanner myObj = new Scanner(System.in);
        System.out.println("Enter a: Protagonist");
        String protagonist = myObj.nextLine();
        System.out.println("Enemy");
        String enemy = myObj.nextLine();
        System.out.println("Desirable Object");
        String object = myObj.nextLine();
        System.out.println("Song");
        String song = myObj.nextLine();
        System.out.println("Integer (ex. 7)");
        int num = myObj.nextInt();
        System.out.println("true or false");
        boolean d = myObj.nextBoolean();
        String end = "";
        if (d){
            end = "Seeking revenge, " + protagonist + " killed " + enemy + ", who had destroyed the " + object + "." ;
        }
        else {
            end = "Seeking revenge, " + protagonist + " attempted to killed " + enemy + ", who had traded the " + object + " for imortality." ;
        }    
        String story = "Whenever " + protagonist + " had " + object + ", the song " + song + " would alsways be at the top of the playlist. \n \n The good days fell short after " + enemy + " stole the " + object + "." + end;
        System.out.println(" ");
        System.out.println(" ");
        System.out.println("The War on " + object);
        System.out.println(" ");
        System.out.println(story);
        System.out.println(" ");
        System.out.println(end);
    }
}
