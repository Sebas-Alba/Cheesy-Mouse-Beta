# Cheesy-Mouse-Beta
//The game consists of evading obstacles that threat the main character.

package application;
	

import javafx.application.Application;
import javafx.event.EventHandler;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.text.Font;
import javafx.scene.text.FontPosture;
import javafx.scene.text.FontWeight;
import javafx.scene.text.Text;
import javafx.stage.Stage;


public class Main extends Application {
	
	
	public void start(Stage Stage) {
	
		Group root = new Group();
		Scene scene = new Scene(root,1200,600);
		
		Text text = new Text("Cheesy Mouse");
		text.setFont(Font.font("Verdana", FontWeight.BOLD, FontPosture.REGULAR,100));
		text.setX(300);
		text.setY(200);
		
		
		Image image = new Image("Cancha.jpg");
		ImageView IV1 = new ImageView();
		IV1.setImage(image);
		IV1.setFitWidth(1200);
		IV1.setFitHeight(600);
			
		
		Button buttonStart = new Button("INCIO");
		buttonStart.setFont(Font.font("Verdana",FontWeight.NORMAL, FontPosture.REGULAR,20));
		buttonStart.setLayoutX(440);
		buttonStart.setLayoutY(460);
		buttonStart.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
				Escenario escenario = new Escenario();
				escenario.CrearEscenario(Stage);
			}
		}
		
		);
		
		Button buttonSalir = new Button("SALIR");
		buttonSalir.setFont(Font.font("verdana",FontWeight.NORMAL, FontPosture.REGULAR,20));
		buttonSalir.setLayoutX(800);
		buttonSalir.setLayoutY(460);
		buttonSalir.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
			System.exit(0);
			}
		}
	
	);
		root.getChildren().addAll(IV1,buttonStart,buttonSalir,text);
		Stage.setScene(scene);
		Stage.show();
	
	}

	public static void main(String[] args) {
		launch(args);
	}

}

package application;

import javafx.event.EventHandler;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.Pane;
import javafx.scene.text.Font;
import javafx.scene.text.FontPosture;
import javafx.scene.text.FontWeight;
import javafx.stage.Stage;

public class Escenario  {
	
	Gatos g = new Gatos ();
	ImageView iv4 = g.enemigo();
	ImageView iv5 = g.enemigo2();
	ImageView iv6 = g.enemigo3();
	
	Pane root = new Pane();
	
	
	
	public void CrearEscenario(Stage stage2)
	{
		Pane root = new Pane();
		Scene scene = new Scene(root,1200,600);
	   
		Image cancha = new Image ("Cancha4.jpg");
		ImageView iv1 = new ImageView();
		iv1.setImage(cancha);
		iv1.setFitWidth(1200);
		iv1.setFitHeight(600);
		
		Image casa = new Image ("Casa.png");
		ImageView iv2 = new ImageView();
		iv2.setImage(casa);
		iv2.setTranslateX(1050);
		iv2.setTranslateY(0);
		iv2.setFitWidth(150);
		iv2.setFitHeight(150);
	
        Image Raton = new Image("Mouse1.png");
		ImageView iv3 = new ImageView();
		iv3.setImage(Raton);
		iv3.setFitWidth(70);
		iv3.setFitHeight(70);
		iv3.setTranslateX(0);
		iv3.setTranslateY(520);
		iv3.setRotate(90);
		
		
		Button buttonSalir = new Button("SALIR");
		buttonSalir.setFont(Font.font("verdana",FontWeight.NORMAL, FontPosture.REGULAR,20));
		buttonSalir.setLayoutX(1100);
		buttonSalir.setLayoutY(560);
		buttonSalir.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
			System.exit(0);
			}
		}
	
	);
		root.getChildren().addAll();
		
		{
	        scene.setOnKeyPressed(event -> {
	            switch (event.getCode()) {
	                case UP:
	                	if(iv3.getTranslateY()>=50) {
	                    	iv3.setTranslateY(iv3.getTranslateY() - 40);
	                    }   
	                	break;
	                	
	                case DOWN:
	                	if(iv3.getTranslateY()<=520) {
	                		iv3.setTranslateY(iv3.getTranslateY() + 40);
	                	}
	                	break;
	                	
	                case LEFT:
	                	if(iv3.getTranslateX()>=10) {
	                		iv3.setTranslateX(iv3.getTranslateX() - 40);
	                	}
	                		break;
	                    
	                case RIGHT:
	                	if(iv3.getTranslateX()<=1050) {
	                		iv3.setTranslateX(iv3.getTranslateX() + 40);
	                	}
	                    break;
	                    
	                default:
	                    break;
	            	}
	        });
	    }
		

	    root.getChildren().addAll(iv1, iv2, iv3, iv4, iv5, iv6, buttonSalir);
	    stage2.setScene(scene);
		stage2.show();
	}
}

package application;

import javafx.animation.Animation;
import javafx.animation.TranslateTransition;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.util.Duration;

public class Gatos {
	
	
	public ImageView enemigo () {
		
		Image Gato1 = new Image("Gato.gif");
		ImageView iv4 = new ImageView();
		iv4.setImage(Gato1);
		iv4.setFitWidth(130);
		iv4.setFitHeight(100);
		iv4.setTranslateX(800);
		iv4.setTranslateY(0);
		iv4.setRotate(-90);
		
		TranslateTransition transition = new TranslateTransition ();
		transition.setDuration(Duration.seconds(1.5));
		transition.setToX(800);
		transition.setToY(500);
		transition.setAutoReverse(true);
		transition.setCycleCount(Animation.INDEFINITE);
		transition.setNode(iv4);
		transition.play();
		
		
		return iv4;
		
	}
	
	public ImageView enemigo2 () {
		
		Image Gato2 = new Image("Gato.gif");
		ImageView iv5 = new ImageView();
		iv5.setImage(Gato2);
		iv5.setFitWidth(130);
		iv5.setFitHeight(100);
		iv5.setTranslateX(750);
		iv5.setTranslateY(400);
		
		TranslateTransition transition2 = new TranslateTransition ();
		transition2.setDuration(Duration.seconds(1.5));
		transition2.setToX(0);
		transition2.setToY(400);
		transition2.setAutoReverse(true);
		transition2.setCycleCount(Animation.INDEFINITE);
		transition2.setNode(iv5);
		transition2.play();
		
		return iv5;
	}
	
	public ImageView enemigo3 () {
		
		Image enemigo3 = new Image("Gato.gif");
		ImageView iv6 = new ImageView();
		iv6.setImage(enemigo3);
		iv6.setFitWidth(130);
		iv6.setFitHeight(100);
		iv6.setTranslateX(700);
		iv6.setTranslateY(200);
		
		TranslateTransition transition3 = new TranslateTransition ();
		transition3.setDuration(Duration.seconds(1.5));
		transition3.setToX(0);
		transition3.setToY(0);
		transition3.setAutoReverse(true);
		transition3.setCycleCount(Animation.INDEFINITE);
		transition3.setNode(iv6);
		transition3.play();
		
		return iv6;
		
	}
}

package application;

public class Posicion {
double px1,py2;
	
	public Posicion ()
	{
	
	}
	public double PosicionRatonX ()
	{
		px1 = 0;
		
		return px1;
	}
	
	public double PosicionRatonY ()
	{
		py2 = 520;
		
		return py2;
	}

}
