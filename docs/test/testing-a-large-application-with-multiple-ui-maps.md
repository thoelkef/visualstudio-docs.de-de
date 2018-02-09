---
title: "Testen einer großen Anwendung mit mehreren UI-Zuordnungen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c2eff9fc8e8aedecb1fd9b99538fa600dbcc5eb1
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Testing a Large Application with Multiple UI Maps

In diesem Thema wird besprochen, wie sich Tests der programmierten UI beim Test einer großen Anwendung mithilfe mehrerer UI-Zuordnungen einsetzen lassen.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
 Beim Erstellen eines neuen Tests der programmierten UI erstellt das Visual Studio-Testframework den Code für den Test standardmäßig in einer <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Klasse. Weitere Informationen zum Aufzeichnen von Tests der programmierten UI finden Sie unter [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md) und [Aufbau von Tests der programmierten UI](../test/anatomy-of-a-coded-ui-test.md).  
  
 Der erzeugte Code für die UI-Zuordnung enthält eine Klasse für jedes Objekt mit der der Test interagiert. Für jede erzeugte Methode wird speziell für diese Methode eine Begleitklasse für Methodenparameter erzeugt. Wenn es eine große Menge an Objekten, Seiten, Formularen und Steuerelementen in der Anwendung gibt, kann die UI-Zuordnung sehr groß werden. Auch wird die Anwendung sehr unhandlich, wenn mehrere Personen an Tests mit einer einzigen, großen UI-Zuordnungsdatei arbeiten.  
  
 Mit mehreren UI-Zuordnungsdateien zu arbeiten hat die folgenden Vorteile:  
  
-   Jede Karte kann einer logischen Teilmenge der Anwendung zugeordnet werden. Damit sind Änderungen einfacher verwaltbar.  
  
-   Jeder Tester kann an einem Abschnitt der Anwendung arbeiten und seinen Code prüfen, ohne dabei andere Tester zu stören, die an anderen Abschnitten der Anwendung arbeiten.  
  
-   Ergänzungen zur Benutzeroberfläche der Anwendung lassen sich inkrementell mit minimalen Auswirkungen auf die Tests an anderen Teilen der Benutzerüberfläche skalieren.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Brauche ich mehrere UI-Zuordnung?  
 Erstellen Sie in jeder der folgenden Situationen UI-Zuordnungen:  
  
-   Verschieden komplexe Sätze zusammengesetzter UI-Steuerelemente, die zusammen einen logischen Vorgang ausführen wie beispielsweise eine Registrierungsseite auf einer Website oder die Kaufseite eines Warenkorbs.  
  
-   Ein unabhängiger Steuerelementsatz, auf den von verschiedenen Punkten der Anwendung aus zugegriffen wird, wie beispielsweise ein Assistent mit verschiedenen Seiten an Vorgängen. Wenn jede Seite eines Assistenten besonders komplex ist, könnten Sie für jede dieser Seiten eine UI-Zuordnung erstellen.  
  
## <a name="adding-multiple-ui-maps"></a>Mehrere UI-Zuordnungen hinzufügen  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>So fügen Sie dem Testprojekt der programmierten UI eine UI-Zuordnung hinzu  
  
1.  Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste die Projektdatei des Coded UI-Tests und erstellen Sie einen Ordner im Coded UI-Test-Projekt, in dem alle UI-Zuordnungen gespeichert werden. Zeigen Sie dazu auf **Hinzufügen**, und wählen Sie **Neuer Ordner**. Sie könnten ihn beispielsweise `UIMaps` nennen.  
  
     Der neue Ordner wird unter dem Coded UI-Test-Projekt angezeigt.  
  
2.  Klicken Sie den Ordner `UIMaps` mit der rechten Maustaste, zeigen Sie auf **Hinzufügen**, und wählen Sie dann **Neues Element** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
    > [!NOTE]
    >  Sie müssen sich in einem Test-Projekt der programmierten UI befinden, um eine neue Testzuordnung der programmierten UI hinzufügen zu können.  
  
3.  Wählen Sie **Testzuordnung der programmierten UI** aus der Liste.  
  
     Geben Sie im Feld **Name** einen Namen für die neue UI-Zuordnung ein. Verwenden Sie den Namen der Komponente oder Seite, für die die Zuordnung steht, beispielsweise `HomePageMap`.  
  
4.  Wählen Sie **Hinzufügen** aus.  
  
     Das Visual Studio-Fenster wird minimiert und das Dialogfeld **Test-Generator der programmierten UI** angezeigt.  
  
5.  Zeichnen Sie Ihr Vorgehen für die erste Methode auf, und wählen Sie **Code generieren**.  
  
6.  Nachdem Sie alle Aktionen und Assertionen für die erste Komponente oder Seite aufgezeichnet und sie in Methoden gruppiert haben, schließen Sie das Dialogfeld **Test-Generator der programmierten UI**.  
  
7.  Erstellen Sie weitere UI-Zuordnungen. Zeichnen Sie die Aktionen und Assertionen auf, gruppieren Sie sie für jede Komponente in Methoden und erstellen Sie den Code.  

 In vielen Fällen bleibt das Fenster auf oberster Ebene für alle Assistenten, Formulare und Seiten gleich. Auch wenn jede UI-Zuordnung eine Klasse für das Fenster auf oberster Ebene hat, verwiesen wahrscheinlich alle Zuordnungen auf dasselbe Fenster auf oberster Ebene, in dem alle Komponenten der Anwendung laufen. Coded UI-Tests suchen hierarchisch von oben nach unten nach Steuerelementen, beginnend vom Fenster auf oberster Ebene. In einer komplexen Anwendung kann das Fenster auf oberster Ebene also in jeder UI-Zuordnung dupliziert werden. Wenn das wirkliche Fenster auf oberster Ebene dupliziert wird, führen Änderungen am Fenster zu mehreren Modifizierungen. Das kann zu Leistungsproblemen führen, wenn man zwischen UI-Zuordnungen wechselt.

 Um diesen Effekt zu minimieren, können Sie die Methode `CopyFrom()` verwenden und damit sicherstellen, dass das neue Fenster auf oberster Ebene in dieser UI-Zuordnung dasselbe wie das Hauptfenster auf oberster Ebene ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel ist Teil einer Hilfsprogrammklasse, die Zugang zu jeder Komponente und deren untergeordneten Steuerelementen verschafft, die durch die in den verschiedenen UI-Zuordnungen erstellen Klassen dargestellt werden.

Zum Beispiel hat eine Webanwendung namens `Contoso` eine Startseite, eine Produktseite und eine Seite mit einem Warenkorb. Jede dieser Seiten teilt ein gemeinsames Fenster auf oberster Ebene, das dem Browserfenster entspricht. Es gibt eine UI-Zuordnung für jede Seite und die Hilfsprogrammklasse hat Code, der dem folgenden entspricht:

```csharp
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

## <a name="see-also"></a>Siehe auch

<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>  
<xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>  
[Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)  
[Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md)  
[Aufbau eines Tests der programmierten UI](../test/anatomy-of-a-coded-ui-test.md)
