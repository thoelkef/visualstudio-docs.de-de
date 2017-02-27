---
title: "Testing a Large Application with Multiple UI Maps | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tests für codierte UI, Für große Anwendungen"
  - "Tests für codierte UI, Mehrere UI-Zuordnungen"
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 22
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 22
---
# Testing a Large Application with Multiple UI Maps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird besprochen, wie sich Coded UI\-Tests beim Test einer großen Anwendung mithilfe mehrerer UI\-Zuordnungen einsetzen lassen.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
 Beim Erstellen eines neuen Coded UI\-Tests erstellt der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Testframework den Code für den Test standardmäßig in einer <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>\-Klasse.  Weitere Informationen zum Aufzeichnen von Tests der programmierten UI finden Sie unter [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) und [Anatomy of a Coded UI Test](../test/anatomy-of-a-coded-ui-test.md).  
  
 Der erzeugte Code für die UI\-Zuordnung enthält eine Klasse für jedes Objekt mit der der Test interagiert.  Für jede erzeugte Methode wird speziell für diese Methode eine Begleitklasse für Methodenparameter erzeugt.  Wenn es eine große Menge an Objekten, Seiten, Formularen und Steuerelementen in der Anwendung gibt, kann die UI\-Zuordnung sehr groß werden.  Auch wird die Anwendung sehr unhandlich, wenn mehrere Personen an Tests mit einer einzigen, großen UI\-Zuordnungsdatei arbeiten.  
  
 Mit mehreren UI\-Zuordnungsdateien zu arbeiten hat die folgenden Vorteile:  
  
-   Jede Karte kann einer logischen Teilmenge der Anwendung zugeordnet werden.  Damit sind Änderungen einfacher verwaltbar.  
  
-   Jeder Tester kann an einem Abschnitt der Anwendung arbeiten und seinen Code prüfen, ohne dabei andere Tester zu stören, die an anderen Abschnitten der Anwendung arbeiten.  
  
-   Ergänzungen zur Benutzeroberfläche der Anwendung lassen sich inkrementell mit minimalen Auswirkungen auf die Tests an anderen Teilen der Benutzerüberfläche skalieren.  
  
## Brauche ich mehrere UI\-Zuordnung?  
 Erstellen Sie in jeder der folgenden Situationen UI\-Zuordnungen:  
  
-   Verschieden komplexe Sätze zusammengesetzter UI\-Steuerelemente, die zusammen einen logischen Vorgang ausführen wie beispielsweise eine Registrierungsseite auf einer Website oder die Kaufseite eines Warenkorbs.  
  
-   Ein unabhängiger Steuerelementsatz, auf den von verschiedenen Punkten der Anwendung aus zugegriffen wird, wie beispielsweise ein Assistent mit verschiedenen Seiten an Vorgängen.  Wenn jede Seite eines Assistenten besonders komplex ist, könnten Sie für jede dieser Seiten eine UI\-Zuordnung erstellen.  
  
## Mehrere UI\-Zuordnungen hinzufügen  
  
#### So fügen Sie dem Testprojekt für codiertes UI eine UI\-Zuordnung hinzu  
  
1.  Klicken Sie in **Projektmappen\-Explorer** mit der rechten Maustaste die Projektdatei des Coded UI\-Tests und erstellen Sie einen Ordner im Coded UI\-Test\-Projekt, in dem alle UI\-Zuordnungen gespeichert werden. Zeigen Sie dazu auf **Hinzufügen** und wählen Sie **Neuer Ordner**.  Sie könnten ihn beispielsweise `UIMaps` nennen.  
  
     Der neue Ordner wird unter dem Coded UI\-Test\-Projekt angezeigt.  
  
2.  Klicken Sie den Ordner `UIMaps` mit der rechten Maustaste, zeigen Sie auf **Hinzufügen** und wählen Sie dann **Neues Element**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
    > [!NOTE]
    >  Sie müssen sich in einem Coded UI\-Test\-Projekt befinden, um eine neue Coded UI\-Testzuordnung hinzufügen zu können.  
  
3.  Wählen Sie **Coded UI\-Testzuordnung** aus der Liste.  
  
     Geben Sie im Feld **Name** einen Namen für die neue UI\-Zuordnung ein.  Verwenden Sie den Namen der Komponente oder Seite, für die die Zuordnung steht, beispielsweise `HomePageMap`.  
  
4.  Wählen Sie **Hinzufügen** aus.  
  
     Das Fenster [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird minimiert und das Dialogfeld **Test\-Generator für codierte UI** angezeigt.  
  
5.  Zeichnen Sie Ihr Vorgehen für die erste Methode auf und wählen Sie **Code generieren**.  
  
6.  Nachdem Sie alle Aktionen und Assertionen für die erste Komponente oder Seite aufgezeichnet und sie in Methoden gruppiert haben, schließen Sie das Dialogfeld **Test\-Generator für codierte UI**.  
  
7.  Erstellen Sie weitere UI\-Zuordnungen.  Zeichnen Sie die Aktionen und Assertionen auf, gruppieren Sie sie für jede Komponente in Methoden und erstellen Sie den Code.  
  
 In vielen Fällen bleibt das Fenster auf oberster Ebene für alle Assistenten, Formulare und Seiten gleich.  Auch wenn jede UI\-Zuordnung eine Klasse für das Fenster auf oberster Ebene hat, verwiesen wahrscheinlich alle Zuordnungen auf dasselbe Fenster auf oberster Ebene, in dem alle Komponenten der Anwendung laufen.  Coded UI\-Tests suchen hierarchisch von oben nach unten nach Steuerelementen, beginnend vom Fenster auf oberster Ebene. In einer komplexen Anwendung kann das Fenster auf oberster Ebene also in jeder UI\-Zuordnung dupliziert werden.  Wenn das wirkliche Fenster auf oberster Ebene dupliziert wird, führen Änderungen am Fenster zu mehreren Modifizierungen.  Das kann zu Leistungsproblemen führen, wenn man zwischen UI\-Zuordnungen wechselt.  
  
 Um diesen Effekt zu minimieren, können Sie die Methode `CopyFrom()` verwenden und damit sicherstellen, dass das neue Fenster auf oberster Ebene in dieser UI\-Zuordnung dasselbe wie das Hauptfenster auf oberster Ebene ist.  
  
## Beispiel  
 Das folgende Beispiel ist Teil einer Hilfsprogrammklasse, die Zugang zu jeder Komponente und deren untergeordneten Steuerelementen verschafft, die durch die in den verschiedenen UI\-Zuordnungen erstellen Klassen dargestellt werden.  
  
 Zum Beispiel hat eine Webanwendung namens `Contoso` eine Startseite, eine Produktseite und eine Seite mit einem Warenkorb.  Jede dieser Seiten teilt ein gemeinsames Fenster auf oberster Ebene, das dem Browserfenster entspricht.  Es gibt eine UI\-Zuordnung für jede Seite und die Hilfsprogrammklasse hat Code, der dem folgenden entspricht:  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anatomy of a Coded UI Test](../test/anatomy-of-a-coded-ui-test.md)