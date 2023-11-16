# JavaFX
JavaFX gaan we nodig hebben bij het volgende project.

We gaan in het volgende project niet op een nieuwe manier leren programmeren. Wel gaan we gebruik maken van lambda-expressies en JavaFX.

JavaFX is voor het userinterface. Vaak is het userinterface in HTML en JS geprogrammeert en dat is ook waar de trend naartoe gaat. JavaFX is nog niet afgeschreven.

Vroeger was het UI gemaakt op een OS-specific manier gemaakt, in Java is dat niet nodig dankzij JavaFX.

We gaan nu een UI aanmaken met een knopje erop. We gaan geen gebruik maken van fxml.

Betere optie dan de code: Gluon SceneBuilder. Net als bij de Challenge.

Observers krijgen we bij OPT3.

```java
// Alle nodige imports hiero
// Wow, wat is deze code onoverzichtelijk.

public class Main extends Application {
  @Override
  public void start(Stage primaryStage) {
    TextField field = new TextField();
    root.setTop(field);
    Button btn = new Button();
  
    btn.setText("Voeg toe'");
    btn.setOnAction(new EventHandler<ActionEvent>() {
      @Override
      public void handle(ActionEvent event) {
        System.out.println("Hello, " + field.getText() + "!");
      }
    });
  
    BorderPain root = new BorderPane();
    root.setBottom(btn);
  
    ListView<String> list = new ListView<String>();
    ObservableList<String> items = FXCollections.observableArrayList("Taak 1", "Taak 2", "Taak 3", "Taak 4");
    items.addListener(new ListChangeListener<String>() {
      @Override
      public void onChanged(Change<? extends String change) {
        System.out.println("Hi");
      }
    });
  
    list.setEditable(true);
    list.setOnEditStart(event -> {
      Stage stage = new Stage();
      stage.setTitle("My new stage title");
      stage.show();
    });
    list.setItems(items);

    field.setText("Voer hier uw naam in");

    Scene scene = new Scene(root, 300, 250);
    primaryStage.setTitle("Hello, World!");
    primaryStage.setScene(scene);
    primaryStage.show();
  }

  public static void main(String[] args) {
    launch(args);
  }
}
```