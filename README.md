# Uebung10

package org.hsd.inflab.Uebung08;

import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.CheckBox;
import javafx.scene.control.ComboBox;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.HBox;
import javafx.stage.Stage;


public class App extends Application {

    @Override
    public void start(Stage stage) {
        
    	try {
    		
    		
    		HBox hbox = new HBox();
    		GridPane gridPane = new GridPane();
    		gridPane.setHgap(10);
    		gridPane.setVgap(20);
    		gridPane.setPadding(new Insets(20));
    		Scene buehne =  new Scene(gridPane,300,200);
    		
    		    		
    		Label labelName = new Label();
    		labelName.setText("Name");
    		
    		Label labelGeburtsjahr = new Label();
    		labelGeburtsjahr.setText("Geburtsjahr");
    		
    		Label labelStand = new Label();
    		labelStand.setText("Stand");
    		
    		TextField textFeld = new TextField();
    		textFeld.setText("Peter Schmitz");
    		
    		ComboBox<String> boxJahre = new ComboBox<>();
    		boxJahre.setEditable(true);
    		boxJahre.setMaxWidth(70);
    		boxJahre.getItems().addAll("1981","1980","1979");
    		boxJahre.getSelectionModel().selectFirst();
    		    		
    		CheckBox checkBox = new CheckBox();
    		checkBox.setText("verheiratet");
    		checkBox.setSelected(true);
    		
    		//Button
    		Button buttonNeu = new Button();
    		buttonNeu.setText("NEU");
    		
    		Button buttonOK = new Button();
    		buttonOK.setText("OK");
    		
    		gridPane.add(labelName, 0, 0);
    		gridPane.add(textFeld, 1, 0,2,1);
    		gridPane.add(labelGeburtsjahr, 0, 1);
    		gridPane.add(boxJahre, 1, 1);
    		gridPane.add(labelStand, 0, 2);
    		gridPane.add(checkBox, 1, 2);
    		
    		gridPane.add(buttonNeu, 2, 3);
    		gridPane.add(buttonOK, 3, 3);
    		
    		stage.setTitle("Personendaten");
    		stage.setScene(buehne);
    		stage.show();
    		
    		//Button Neue angeklickt wird
    		
    		buttonNeu.setOnAction(new EventHandler<ActionEvent>() {
				
				@Override
				public void handle(ActionEvent event) {

					textFeld.setText("Peter Schmitz");
					boxJahre.getSelectionModel().selectFirst();
					checkBox.setSelected(true);
					
				}
			});
    		
    		//Wenn Ok angeklickt wird
    		buttonOK.setOnAction(new EventHandler<ActionEvent>() {
				
				@Override
				public void handle(ActionEvent event) {
					String nameTemp;
		    		String geburtsjahrTemp;
		    		Boolean standTemp;
		    		
					nameTemp = textFeld.getText();
					geburtsjahrTemp = boxJahre.getSelectionModel().getSelectedItem();
					standTemp = checkBox.isSelected();
					
					Person person = new Person(nameTemp, geburtsjahrTemp, standTemp);
					
//					System.out.println("Name: " + person.name);
//					System.out.println("geburtsjahrTemp: " + geburtsjahrTemp);
//					System.out.println("standTemp: " + standTemp);
					
				}
			});
    		
    	}
    	catch (Exception e) {
    		e.printStackTrace();    		
    	}
    }

    public static void main(String[] args) {
        launch();
    }

}


//############################################################################## Person

package org.hsd.inflab.Uebung08;

public class Person {
	
	String name;
	String geburtsjahr;
	Boolean verheiratet;
	
	public Person(String name, String geburtsjahr, Boolean verheiratet){
		
		this.name = name;
		this.geburtsjahr = geburtsjahr;
		this.verheiratet = verheiratet;
		
	}

}
