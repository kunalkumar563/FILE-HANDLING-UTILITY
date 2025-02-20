import java.io.*;
public class FileOperations {
    
    public static void writeToFile(String filename, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filename))) {
            writer.write(content);
            System.out.println("Content written to " + filename);
        } catch (IOException e) {
            System.out.println("Error writing to file: " + e.getMessage());
        }
    }
    
    public static void readFromFile(String filename) {
        try (BufferedReader reader = new BufferedReader(new FileReader(filename))) {
            String line;
            System.out.println("Content read from " + filename + ":");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (FileNotFoundException e) {
            System.out.println("Error: " + filename + " not found.");
        } catch (IOException e) {
            System.out.println("Error reading from file: " + e.getMessage());
        }
    }
    
    public static void appendToFile(String filename, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filename, true))) {
            writer.write(content);
            System.out.println("Content appended to " + filename);
        } catch (IOException e) {
            System.out.println("Error appending to file: " + e.getMessage());
        }
    }
    
    public static void main(String[] args) {
        String filename = "sample.txt";
        
        // Writing to the file
        writeToFile(filename, "Hello, this is a sample file.\n");
        
        // Reading from the file
        readFromFile(filename);
        
        // Appending to the file
        appendToFile(filename, "This is an appended line.\n");
        
        // Reading again to confirm append
        readFromFile(filename);
    }
}
