---
title: "L2DBForm.xaml.cs – Quellcode | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 2
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 484ffe617123e6daf147210761e0fa9dd60bd379
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="l2dbformxamlcs-source-code"></a>L2DBForm.xaml.cs Source Code
Dieses Thema enthält den Inhalt und die Beschreibung des C#-Quellcodes in der Datei <legacyBold>L2DBForm.xaml.cs</legacyBold>. Die in dieser Datei enthaltene <legacyBold>L2XDBForm</legacyBold>-Teilklasse kann in die folgenden drei logischen Abschnitte unterteilt werden: Datenmember und die Ereignishandler `OnRemove` und `OnAddBook` für das Klicken auf Schaltflächen.  
  
## <a name="data-members"></a>Datenmember  
 Für die Zuordnung dieser Klasse zu den in <legacyBold>L2DBForm.xaml</legacyBold> verwendeten Fensterressourcen werden zwei private Datenmember verwendet.  
  
-   Die `myBooks`-Namespacevariable wird mit `"http://www.mybooks.com"` initialisiert.  
  
-   Der `bookList`-Member wird im Konstruktor mit der folgenden Zeile in die CDATA-Zeichenfolge in <legacyBold>L2DBForm.xaml</legacyBold> initialisiert:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## <a name="onaddbook-event-handler"></a>"OnAddBook"-Ereignishandler  
 Diese Methode enthält die folgenden drei Anweisungen:  
  
-   Die erste Bedingungsanweisung wird zur Eingabevalidierung verwendet.  
  
-   Die zweite Anweisung erstellt aus den Zeichenfolgenwerten, die der Benutzer im Benutzeroberflächenabschnitt **Add New Book** eingegeben hat, ein neues <xref:System.Xml.Linq.XElement>.  
  
-   Die letzte Anweisung fügt dem Datenanbieter in <legacyBold>L2DBForm.xaml</legacyBold> dieses neue Buchelement hinzu. Daraufhin aktualisiert die dynamische Datenbindung automatisch die Benutzeroberfläche mit diesem neuen Element. Zusätzlicher, vom Benutzer bereitgestellter Code ist nicht erforderlich.  
  
## <a name="onremove-event-handler"></a>"OnRemove"-Ereignishandler  
 Der `OnRemove`-Handler ist aus zwei Gründen komplizierter als der `OnAddBook`-Handler. Erstens: Das unformatierte XML enthält beibehaltenen Leerraum, sodass zusammen mit dem Bucheintrag auch  passende neue Zeilen entfernt werden müssen. Zweitens: Im Sinne der Bequemlichkeit wird die Auswahl, die auf dem gelöschten Element lag, auf das vorherige Element in der Liste zurückgesetzt.  
  
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
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
  
### <a name="code"></a>Code  
  
```csharp  
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
  
### <a name="comments"></a>Kommentare  
 Informationen zur zugeordneten XAML-Quelle für diese Handler finden Sie unter [L2DBForm.xaml.cs – Quellcode](../designers/l2dbform-xaml-source-code.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiel](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [L2DBForm.xaml-Quellcode](../designers/l2dbform-xaml-source-code.md)
