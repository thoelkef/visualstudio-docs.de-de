---
title: "Quellcode in der Datei &#39;L2DBForm.xaml.cs&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Quellcode in der Datei &#39;L2DBForm.xaml.cs&#39;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Thema enthält den Inhalt und die Beschreibung des C\#\-Quellcodes in der Datei **L2DBForm.xaml.cs**.Die in dieser Datei enthaltene **L2XDBForm**\-Teilklasse kann in die folgenden drei logischen Abschnitte unterteilt werden: Datenmember und die Ereignishandler `OnRemove` und `OnAddBook` für das Klicken auf Schaltflächen.  
  
## Datenmember  
 Für die Zuordnung dieser Klasse zu den in **L2DBForm.xaml** verwendeten Fensterressourcen werden zwei private Datenmember verwendet.  
  
-   Die `myBooks`\-Namespacevariable wird mit `"http://www.mybooks.com"` initialisiert.  
  
-   Der `bookList`\-Member wird im Konstruktor mit der folgenden Zeile in die CDATA\-Zeichenfolge in **L2DBForm.xaml** initialisiert:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## "OnAddBook"\-Ereignishandler  
 Diese Methode enthält die folgenden drei Anweisungen:  
  
-   Die erste Bedingungsanweisung wird zur Eingabevalidierung verwendet.  
  
-   Die zweite Anweisung erstellt aus den Zeichenfolgenwerten, die der Benutzer im Benutzeroberflächenabschnitt **Add New Book** eingegeben hat, ein neues <xref:System.Xml.Linq.XElement>.  
  
-   Die letzte Anweisung fügt dem Datenanbieter in **L2DBForm.xaml** dieses neue Buchelement hinzu.Daraufhin aktualisiert die dynamische Datenbindung automatisch die Benutzeroberfläche mit diesem neuen Element. Zusätzlicher, vom Benutzer bereitgestellter Code ist nicht erforderlich.  
  
## "OnRemove"\-Ereignishandler  
 Der `OnRemove`\-Handler ist aus zwei Gründen komplizierter als der `OnAddBook`\-Handler.Erstens: Das unformatierte XML enthält beibehaltenen Leerraum, sodass zusammen mit dem Bucheintrag auch  passende neue Zeilen entfernt werden müssen.Zweitens: Im Sinne der Bequemlichkeit wird die Auswahl, die auf dem gelöschten Element lag, auf das vorherige Element in der Liste zurückgesetzt.  
  
 Die Hauptarbeit, das Entfernen des ausgewählten Buchelements, wird aber von lediglich zwei Anweisungen erledigt:  
  
-   Zunächst wird das dem aktuell ausgewählten Element im Listenfeld zugeordnete Buchelement abgerufen:  
  
    ```  
    XElement selBook = (XElement)lbBooks.SelectedItem;   
    ```  
  
-   Anschließend wird dieses Element aus dem Datenanbieter gelöscht:  
  
    ```  
    selBook.Remove();  
    ```  
  
 Auch hier stellt die dynamische Datenbindung sicher, dass die Benutzeroberfläche des Programms automatisch aktualisiert wird.  
  
## Beispiel  
  
### Beschreibung  
  
### Code  
  
```c#  
using System;  
using System.Linq;  
using System.Collections;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Input;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace LinqToXmlDataBinding {  
    /// <summary>  
    /// Interaction logic for L2XDBForm.xaml  
    /// </summary>  
  
    public partial class L2XDBForm : System.Windows.Window   
    {  
        XNamespace mybooks = "http://www.mybooks.com";  
        XElement bookList;  
  
        public L2XDBForm()   
        {  
            InitializeComponent();  
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
        }  
  
        void OnRemoveBook(object sender, EventArgs e)   
        {  
            int index = lbBooks.SelectedIndex;  
            if (index < 0) return;  
  
            XElement selBook = (XElement)lbBooks.SelectedItem;  
            //Get next node before removing element.  
            XNode nextNode = selBook.NextNode;  
            selBook.Remove();  
  
            //Remove any matching newline node.  
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))  
            { nextNode.Remove(); }  
  
            //Set selected item.   
            if (lbBooks.Items.Count > 0)  
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }  
        }  
  
        void OnAddBook(object sender, EventArgs e)   
        {  
            if (String.IsNullOrEmpty(tbAddID.Text) ||  
                String.IsNullOrEmpty(tbAddValue.Text))  
            {  
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");  
                return;   
            }  
            XElement newBook = new XElement(  
                                mybooks + "book",  
                                new XAttribute("id", tbAddID.Text),  
                                tbAddValue.Text);  
            bookList.Add("  ", newBook, "\r\n");  
        }  
    }  
}  
  
```  
  
### Kommentare  
 Informationen zur zugeordneten XAML\-Quelle für diese Handler finden Sie unter [L2DBForm.xaml\-Quellcode](../designers/l2dbform-xaml-source-code.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: 'LinqToXmlDataBinding'\-Beispiel](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [L2DBForm.xaml\-Quellcode](../designers/l2dbform-xaml-source-code.md)