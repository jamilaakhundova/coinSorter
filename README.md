
package CoinSorter;

import java.util.*;

public class CoinSorter
{
	// initializing the variables and create a constructor
	
	private String curr;
	private int minCoin = 0;
	private int maxCoin = 10000;
	private List<Integer> coinListInitial = new ArrayList<>();

	// creating class constructor
	public CoinSorter (String currency, int minCoinIn, int maxCoinIn, List<Integer> coinList)
	{
		currency = curr;
		minCoinIn = minCoin;
		maxCoinIn = maxCoin;
		coinList = coinListInitial;	
		coinListInitial.add(200);
		coinListInitial.add(100);
		coinListInitial.add(50);
		coinListInitial.add(20);
		coinListInitial.add(10);
	};
	// adding elements to the list
	public void CoinSorter() 
	{
				coinListInitial.add(200);
				coinListInitial.add(100);
				coinListInitial.add(50);
				coinListInitial.add(20);
				coinListInitial.add(10);
	}
	
	// GETters and SETters
	public void setCurrency (String currency) 
	{
		curr = currency;
	}
	
	public void setMinCoinIn (int minCoinIn)
	{
		minCoin = minCoinIn;
	}
	
	public void setMaxCoinIn (int maxCoinIn)
	{
		maxCoin = maxCoinIn;
	}
	
	public String getCurrency() 
	{
		return curr;
	}
	
	public int getMinCoinIn()
	{
		return minCoin;
	}
	
	public int getMaxCoinIn()
	{
		return maxCoin;
	}
	
	// Print coin list from the available coin types
	public String printCoinList()
	{
		return "The following coin denominations are in circulation: £2, £1, 50p, 20p, 10p." + "\n" + "The coin denominations should be inputed only in a numerical format: 2, 1, 50, 20, 10." + "\n" + "Note#1: £1 equals to 100p." + "\n" + "Note#1: £2 equals to 200p.";
	}
	
	// function to calculate coins
	public String coinCalculator(int totalSum, int coinType) 
	{
		// validate the inputs before continuing
		if (totalSum < getMinCoinIn() || totalSum > getMaxCoinIn()) {
			return "The minimum input number is 0 and maximum input number is 10000. Please refer to Program Configurations for detailed information on the possible input.";
			} else if (coinType != 10 && coinType != 20 && coinType != 50 && coinType != 100 && coinType != 200){
				return "The accepted coin types are 200p (£2), 100p (£1), 50p, 20p, 10p. The coin type should be inputed as an integer.";
			} else 
			{ 
		int result = totalSum/coinType;
		int remainder = totalSum % coinType;
		return "A total of " + result + " × " + coinType + "p coins can be exchanged. The remainder of the operation is " + remainder + ".";
			}
	}
	
	// function to calculate MultiCoinCalculator
	public String multiCoinCalculator(int totalValue, int coinExclude)
	// validating the input before going on with the function
	{	if (totalValue < getMinCoinIn() || totalValue > getMaxCoinIn()) {
		return "The minimum input number is 0 and maximum input number is 10000. Please refer to Program Configurations for detailed informaiton on the possible input.";
	} 	else if (coinExclude != 10 && coinExclude != 20 && coinExclude != 50 && coinExclude != 100 && coinExclude != 200) {
		return "The accepted coin types are 200p (£2), 100p (£1), 50p, 20p, 10p. The coin type should be inputed as an integer.";
	}   else 
	{
		StringBuilder finalResult = new StringBuilder();
		finalResult.append("The coins exchanged are:");
		int size = coinListInitial.size();
		for (int i=0; i<size;i++) {
		if (coinListInitial.get(i) == coinExclude)
		{
			finalResult.append(0 + " × " + coinListInitial.get(i) + "p, ");
		} else 
		{
			finalResult.append(totalValue/coinListInitial.get(i) + " x " + coinListInitial.get(i) + "p, ");
			totalValue = totalValue % coinListInitial.get(i);
		}
		}
		finalResult.append("with a reminder of " + totalValue + " p.");
		return finalResult.toString();
		
	}
	}
	
	// function to display Program Configurations
	public String displayProgramConfigs()
	{
		return "Currency. The default used currency is pounds." + "\n" + "Minimum value. The minimum accepted value is 0 pence." + "\n" + "Maximum value. The maximum accepted value is 10000 pence.";
	}
}










testCoinSorter
package CoinSorter;

import java.util.*;

import java.lang.*;

public class testCoinSorter {
	
	public static void main(String[] args) {
		int choice;
		CoinSorter coin=new CoinSorter("", 0, 0, new ArrayList<Integer>());
		do 
		{
			System.out.println("***Coin Sorter - MainMenu***");
			System.out.println("1 - Coin Calculator");
			System.out.println("2 - Multiple Coin Calculator");
			System.out.println("3 - Print Coin List");
			System.out.println("4 - Set Details");
			System.out.println("5 - Display program configurations");
			System.out.println("6 - Quit the program");
			System.out.println();
			System.out.println("Please enter the menu number:");
			
			Scanner textMenu = new Scanner(System.in);
			choice = textMenu.nextInt();
			System.out.println();
			switch (choice)
			{
			case 1:
				int totalSum;
				int coinType;
				do {
				System.out.println("Enter the total value to exchange:");
				totalSum = textMenu.nextInt();
				System.out.println("Enter a coin type in which the exchange should be proceeded:");
				coinType = textMenu.nextInt();
				System.out.println(coin.coinCalculator(totalSum, coinType));
				System.out.println();
				} while ((totalSum < 0 || totalSum > 10000) && coinType != 200 && coinType != 100 && coinType != 50 && coinType != 20 && coinType != 10);
				System.out.println();
				break;
			case 2:
				int totalValue;
				int coinExclude;
				do { System.out.println("Enter the total value to exchange:"); 
				totalValue = textMenu.nextInt();} while (totalValue < 0 || totalValue > 10000);
				do { System.out.println("Enter a coin type that should be excluded:");
				coinExclude = textMenu.nextInt();} while (coinExclude != 200 && coinExclude != 100 && coinExclude != 50 && coinExclude != 20 && coinExclude != 10);
				System.out.println(coin.multiCoinCalculator(totalValue, coinExclude));
				System.out.println();
				break;
			case 3:
				System.out.println(coin.printCoinList());
				System.out.println();
				break;
			case 4:
				int choice2;
				do
				{
				System.out.println("***Set Details Sub-Menu***");
				System.out.println("1 - Set currency");
				System.out.println("2 - Set minimum coin input value");
				System.out.println("3 - Set maximum coin input value");
				System.out.println("4 - Return to main menu");
				choice2 = textMenu.nextInt();
				switch (choice2)
					{
				case 1:
					String currency;
					String defaultCurrency = "pounds";					
					do {
					System.out.println("Refer to program configurations for more info. Please enter a default currency:");
					currency = textMenu.next();
					coin.setCurrency(currency);
					} while (!currency.equalsIgnoreCase(defaultCurrency));
					break;
				case 2:
					int minCoinIn;
					do {
					System.out.println("Refer to program configurations for more info. Please enter a minimum coin input value:");
					minCoinIn = textMenu.nextInt();
					coin.setMinCoinIn(minCoinIn);
					} while (minCoinIn < 0);
					break;
				case 3:
					int maxCoinIn;
					do {
					System.out.println("Please enter a maximum coin input value:");
					maxCoinIn = textMenu.nextInt();
					coin.setMaxCoinIn(maxCoinIn);
					} while (maxCoinIn > 10000);
					break;
				default:
					if (choice != 4) System.out.println("Unknown option");
					break;
					}
				} while (choice != 4);
			case 5:
				System.out.println(coin.displayProgramConfigs());
				System.out.println();
				break;
			default:
				if (choice != 6) System.out.println("Unknown option");
				break;
				}
			
		}
		while (choice!=6);
		System.out.println("Have a nice day!");

	}
	


}


















CoinSorterGUI
package CoinSorter;

import java.util.ArrayList;
import javafx.application.Application;
import javafx.application.Platform;
import javafx.geometry.Pos; 
import javafx.scene.Scene; 
import javafx.scene.control.Button; 
import javafx.scene.control.Label; 
import javafx.scene.control.TextArea; 
import javafx.scene.control.TextField;
import javafx.scene.layout.Background;
import javafx.scene.layout.HBox; 
import javafx.scene.layout.VBox; 
import javafx.scene.paint.Color; 
import javafx.scene.text.Font;
import javafx.scene.text.Text;
import javafx.stage.Stage; 
	
public class CoinSorterGUI extends Application
{
	private CoinSorter textCS = new CoinSorter("", 0, 0, new ArrayList<Integer>());
	
	public void start(Stage stage)
	{
		 Text caption = new Text(68, 240, "***Coin Sorter - Main Menu***");         
		 caption.setFill(Color.RED);         
		 caption.setFont(Font.font ("Verdana", 20));
		 
		 Button option1 = new Button("1 - Coin Calculator");
		 Button option2 = new Button("2 - Multiple Coin Calculator");
		 Button option3 = new Button("3 - Print Coin List");
		 Button option4 = new Button("4 - Set Details");
		 Button option5 = new Button("5 - Display Program Configurations");
		 Button option6 = new Button("6 - Quit the program");
		 
		 HBox optionBox = new HBox(20);         
		 optionBox.setAlignment(Pos.CENTER);      
		 optionBox.getChildren().addAll(option1, option2, option3, option4, option5, option6);
		 
		 VBox container = new VBox(50);
		 container.setBackground(Background.EMPTY);         
		 container.setAlignment(Pos.CENTER);
		 container.getChildren().addAll(optionBox, caption);
		 Scene scene = new Scene(container, 250, 275, Color.WHITE);
		 
		 // Elements for Coin Calculator
		 
		 	TextField totalSum = new TextField();         
			totalSum.setMaxWidth(40);         
			TextField coinType = new TextField();         
			coinType.setMaxWidth(40); 
	
			TextArea displayCC = new TextArea();        
			displayCC.setEditable(false);         
			displayCC.setMinSize(210,40);         
			displayCC.setMaxSize(210,40); 
			
			Label totalSumLabel = new Label("Total value to exchange");         
			totalSumLabel.setTextFill(Color.BLUE);         
			totalSumLabel.setFont(Font.font("Arial", 20));         
			Label coinTypeLabel= new Label("Coin type to use");         
			coinTypeLabel.setTextFill(Color.RED);         
			coinTypeLabel.setFont(Font.font("Arial", 20));
		 
			Button calculateCCButton = new Button();         
			calculateCCButton.setText("Calculate");  
			
			Text coinCalculator = new Text(68, 240, "***Coin Calculator***");         
			coinCalculator.setFill(Color.RED);         
			coinCalculator.setFont(Font.font ("Verdana", 20));
			
     		HBox h1 = new HBox(50);
			h1.setAlignment(Pos.CENTER);      
			h1.getChildren().addAll(totalSum, coinType, totalSumLabel, coinTypeLabel, displayCC);
			VBox v1 = new VBox(50);
			v1.setBackground(Background.EMPTY);         
			v1.setAlignment(Pos.CENTER);
			v1.getChildren().addAll(coinCalculator, h1, calculateCCButton);
			Scene scene1 = new Scene(v1, 250, 275, Color.YELLOW);
			
			
			
		// Elements for Multi Coin Calculator
			TextField totalValue = new TextField();         
			totalSum.setMaxWidth(40);         
			TextField coinExclude = new TextField();         
			coinType.setMaxWidth(40); 
	
			TextArea displayMC = new TextArea();        
			displayMC.setEditable(false);         
			displayMC.setMinSize(210,40);         
			displayMC.setMaxSize(210,40); 
			
			Label totalValueLabel = new Label("Total value to exchange");         
			totalValueLabel.setTextFill(Color.BLUE);         
			totalValueLabel.setFont(Font.font("Arial", 20));         
			Label coinExcludeLabel= new Label("Coin type to use");         
			coinExcludeLabel.setTextFill(Color.RED);         
			coinExcludeLabel.setFont(Font.font("Arial", 20));
		 
			Button calculateMCButton = new Button();         
			calculateMCButton.setText("Calculate");  
			
			Text multiCoinCalculator = new Text(68, 240, "***Multi Coin Calculator***");         
			multiCoinCalculator.setFill(Color.RED);         
			multiCoinCalculator.setFont(Font.font ("Verdana", 20));
			
			HBox h2 = new HBox(50);
			h2.setAlignment(Pos.CENTER);      
			h2.getChildren().addAll(totalValue, coinExclude, totalValueLabel, coinExcludeLabel, displayMC);
			VBox v2 = new VBox(50);
			v2.setBackground(Background.EMPTY);         
			v2.setAlignment(Pos.CENTER);
			v2.getChildren().addAll(multiCoinCalculator, h2, calculateMCButton);
			Scene scene2 = new Scene(v1, 250, 275, Color.CORAL);
			
		// Elements for Print Coin List
			Text printCoinList = new Text(68, 240, "***Print Coin List***");         
			printCoinList.setFill(Color.RED);         
			printCoinList.setFont(Font.font ("Verdana", 20));
			
			TextArea displayCL = new TextArea(textCS.printCoinList());        
			displayCL.setEditable(false);         
			displayCL.setMinSize(210,40);         
			displayCL.setMaxSize(210,40); 
			
			HBox h3 = new HBox(50);
			h3.setAlignment(Pos.CENTER);      
			h3.getChildren().addAll(displayCL);
			VBox v3 = new VBox(50);
			v3.setBackground(Background.EMPTY);         
			v3.setAlignment(Pos.CENTER);
			v3.getChildren().addAll(h3, printCoinList);
			Scene scene3 = new Scene(v1, 250, 275, Color.AQUAMARINE);
		
		//  Elements of Set Details Menu
			Text setDetailsMenu = new Text(68, 240, "**Set Details Sub-Menu**");
		    setDetailsMenu.setFill(Color.RED);
		    setDetailsMenu.setFont(Font.font ("Verdana", 20));

		    Button button1 = new Button("1 - Set Currency");
		    Button button2 = new Button("2 - Set minimum coin input value");
		    Button button3 = new Button("3 - Set maximum coin input value");
		    Button button4 = new Button("4 - Return to main menu");

		    HBox h4 = new HBox(50);
		    h4.setAlignment(Pos.CENTER);
		    h4.getChildren().addAll(button1, button2, button3, button4);

		    VBox v4 = new VBox(50);
		    v4.setBackground(Background.EMPTY);
		    v4.setAlignment(Pos.CENTER);
		    v4.getChildren().addAll(h4, setDetailsMenu);
		    Scene scene4 = new Scene(v4, 250, 275, Color.WHITE); 
			
		 // Button 1 elements
		    Text setCurrency = new Text(68, 240, "*Set Currency*");
		    setCurrency.setFill(Color.HOTPINK);
		    setCurrency.setFont(Font.font ("Verdana", 20));
		    
		    TextField Currency = new TextField();         
			Currency.setMaxWidth(40);  
			
			Label CurrencyLabel = new Label("Set Currency");         
			CurrencyLabel.setTextFill(Color.BLACK);         
			CurrencyLabel.setFont(Font.font("Arial", 20));  
			
			Button currencyButton = new Button("Set Currency");
			
			HBox h41 = new HBox(50);
			h41.setAlignment(Pos.CENTER);
		    h41.getChildren().addAll(Currency, CurrencyLabel, currencyButton);
		    
		    TextArea displayButton1 = new TextArea();        
		    displayButton1.setEditable(false);         
		    displayButton1.setMinSize(210,40);         
		    displayButton1.setMaxSize(210,40); 

		    VBox v41 = new VBox(50);
		    v41.setBackground(Background.EMPTY);
		    v41.setAlignment(Pos.CENTER);
		    v41.getChildren().addAll(h41, setCurrency);
		    Scene scene41 = new Scene(v41, 250, 275, Color.WHITE);	
		    
		//	Button 2 elements
		    Text setMinValue = new Text(68, 240, "*Minimum Value*");
		    setMinValue.setFill(Color.LAVENDERBLUSH);
		    setMinValue.setFont(Font.font ("Verdana", 20));
		    
		    TextField minValue = new TextField();         
		    minValue.setMaxWidth(40);  
			
			Label minValueLabel = new Label("*Set Minimum Value*");         
			minValueLabel.setTextFill(Color.SALMON);         
			minValueLabel.setFont(Font.font("Arial", 20));  
			
		    TextArea displayButton2 = new TextArea();        
		    displayButton2.setEditable(false);         
		    displayButton2.setMinSize(210,40);         
		    displayButton2.setMaxSize(210,40); 
			
			Button minValueButton = new Button("Set Value");
			
			HBox h42 = new HBox(50);
			h42.setAlignment(Pos.CENTER);
		    h42.getChildren().addAll(minValue, minValueLabel, minValueButton);

		    VBox v42 = new VBox(50);
		    v42.setBackground(Background.EMPTY);
		    v42.setAlignment(Pos.CENTER);
		    v42.getChildren().addAll(h42, setMinValue);
		    Scene scene42 = new Scene(v42, 250, 275, Color.WHITE);	
		    
		//  Button 3 elements
		    Text setMaxValue = new Text(68, 240, "*Maximum Value*");
		    setMinValue.setFill(Color.LAVENDERBLUSH);
		    setMinValue.setFont(Font.font ("Verdana", 20));
		    
		    TextField maxValue = new TextField();         
		    maxValue.setMaxWidth(40);  
			
			Label maxValueLabel = new Label("Set Value");         
			maxValueLabel.setTextFill(Color.MAROON);         
			maxValueLabel.setFont(Font.font("Arial", 20));  
			
		    TextArea displayButton3 = new TextArea();        
		    displayButton3.setEditable(false);         
		    displayButton3.setMinSize(210,40);         
		    displayButton3.setMaxSize(210,40); 
			
			Button maxValueButton = new Button("Set Value");
			
			HBox h43 = new HBox(50);
			h43.setAlignment(Pos.CENTER);
		    h43.getChildren().addAll(maxValue, maxValueLabel, maxValueButton);

		    VBox v43 = new VBox(50);
		    v43.setBackground(Background.EMPTY);
		    v43.setAlignment(Pos.CENTER);
		    v43.getChildren().addAll(h43, setMaxValue);
		    Scene scene43 = new Scene(v43, 250, 275, Color.WHITE);	
		    
		//  Elements of Display Program Configurations
		    
		    Text displayProgramConfigs = new Text(68, 240, "***Program Configurations***");         
		    displayProgramConfigs.setFill(Color.GREENYELLOW);         
		    displayProgramConfigs.setFont(Font.font ("Verdana", 20));
			
			TextArea displayPC = new TextArea(textCS.displayProgramConfigs());        
			displayPC.setEditable(false);         
			displayPC.setMinSize(210,40);         
			displayPC.setMaxSize(210,40); 
			
			HBox h5 = new HBox(50);
			h5.setAlignment(Pos.CENTER);      
			h5.getChildren().addAll(displayPC);
			VBox v5 = new VBox(50);
			v5.setBackground(Background.EMPTY);         
			v5.setAlignment(Pos.CENTER);
			v5.getChildren().addAll(h5, displayProgramConfigs);
			Scene scene5 = new Scene(v1, 250, 275, Color.AQUAMARINE);
		    
		//  Actions of options
			option1.setOnAction(e -> 
			{
				stage.setScene(scene1);
				stage.setTitle("Coin Calculation");
				stage.show();
				
			});
			
			calculateCCButton.setOnAction( e ->                     
			{   
   
				if(totalSum.getText().isEmpty() || coinType.getText().isEmpty())        
				{                               
					displayCC.setText("Total Value and Coin Type must be entered");                       
				}  
				else                        
				{     
  				displayCC.setText(textCS.coinCalculator(Integer.parseInt(totalSum.getText()), Integer.parseInt(coinType.getText())));                         
				}                                                                        
			}                                     
			); 
			
			option2.setOnAction(e ->
			{
			stage.setScene(scene2);
			stage.setTitle("Multi Coin Calculator");
			stage.show();
			}
			);
			
			calculateMCButton.setOnAction( e ->                     
			{   
   
				if(totalValue.getText().isEmpty() || coinExclude.getText().isEmpty())        
				{                               
					displayMC.setText("Total Value and Coin type to be excluded must be entered");                       
				}  
				else                        
				{     
  				displayMC.setText(textCS.multiCoinCalculator(Integer.parseInt(totalValue.getText()), Integer.parseInt(coinExclude.getText())));                         
				}                                                                        
			}                                     
			);
			
			option3.setOnAction(e ->
			{
			stage.setScene(scene3);
			stage.setTitle("Print Coin List");
			stage.show();
			}
			);
			
			option4.setOnAction(e ->
			{
				stage.setScene(scene4);
				stage.setTitle("Set Details");
				stage.show();
			}
			);
			
			// Option4 buttons' actions
			
			button1.setOnAction(e ->
			{
				stage.setScene(scene41);
				stage.setTitle("Set Currency");
				stage.show();
			}
					);
			
			currencyButton.setOnAction( e ->                     
			{   
   
				if(Currency.getText().isEmpty())        
				{                               
					displayButton1.setText("Please enter a currency to be set.");                       
				}  
				else                        
				{     
  				textCS.setCurrency(Currency.getText());
				displayButton1.setText(textCS.getCurrency());                         
				}                                                                      
			}                                     
			);
			
			button2.setOnAction(e ->
			{
				stage.setScene(scene42);
				stage.setTitle("Set Minimum Value");
				stage.show();
			}
					);
			
			minValueButton.setOnAction( e ->                     
			{   
   
				if(minValue.getText().isEmpty())        
				{                               
					displayButton2.setText("Please enter a minimum value to be set.");                       
				}  
				else                        
				{     
  				textCS.setMinCoinIn(Integer.parseInt(setMinValue.getText()));
  				
				}                                                                        
			}                                     
			);
			
			button3.setOnAction(e ->
			{
				stage.setScene(scene43);
				stage.setTitle("Set Maximum Value");
				stage.show();
			}
					);
			
			maxValueButton.setOnAction( e ->                     
			{   
   
				if(minValue.getText().isEmpty())        
				{                               
					displayButton3.setText("Please enter a maximum value to be set.");                       
				}  
				else                        
				{     
  				textCS.setMaxCoinIn(Integer.parseInt(setMaxValue.getText()));
  				
				}                                                                        
			}                                     
			);
			
			button4.setOnAction(e ->
			{
				stage.setScene(scene);
				stage.show();
			}
					);
			
			option5.setOnAction(e ->
			{
			stage.setScene(scene5);
			stage.setTitle("Print Program Configurations");
			stage.show();
			}
			);
			
			option6.setOnAction(e ->
			{
				Platform.exit();
			}
					);
			
		 stage.setScene(scene);
		 stage.setTitle("Coin Sorting Machine");
		 stage.show();
	}
	
	 public static void main(String[] args)     
	 {         
		 launch(args);     
	 } 
}



















testCoinSorterGUI
package CoinSorter;

import java.util.*;

public class testCoinSorterGUI

{
	CoinSorterGUI sorter = new CoinSorterGUI();
    
	public static void main(String[] args)     
    {         
    	CoinSorterGUI.main(null);
    } 
}
