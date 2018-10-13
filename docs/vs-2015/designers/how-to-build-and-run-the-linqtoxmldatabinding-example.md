---
title: 'Vorgehensweise: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e299000cd8477ccc36829e806072cb25e115f8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237912"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Gewusst wie: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird gezeigt, wie Sie das Visual Studio-<legacyBold>LinqToXmlDataBinding</legacyBold>-Projekt erstellen und das resultierende WPF-<legacyBold>LinqToXmlDataBinding</legacyBold>-Beispielprogramm ausführen können.  
  
 Weitere Informationen zum Verwenden von Visual Studio für das Erstellen von Projekten finden Sie unter [Anwendungsentwicklung in Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Erstellen und Auffüllen des Projekts  
  
#### <a name="to-create-the-starting-project"></a>So erstellen Sie das Startprojekt  
  
1.  Starten Sie Visual Studio, und erstellen Sie eine C#-WPF-Anwendung mit dem Namen <legacyBold>LinqToXmlDataBinding</legacyBold>. Das Projekt muss .NET Framework 3.5 (oder höher) verwenden.  
  
2.  Sofern nicht bereits vorhanden, fügen Sie Projektverweise für die folgenden .NET-Assemblys hinzu:  
  
    -   <legacyBold>System.Data</legacyBold>  
  
    -   <legacyBold>System.Data.DataSetExtensions</legacyBold>  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Erstellen Sie die Projektmappe, indem Sie **STRG+UMSCHALT+B** drücken, und führen Sie sie dann mit **F5** aus. Das Projekt sollte ohne Fehler kompiliert und als generische WPF-Anwendung ausgeführt werden.  
  
#### <a name="to-add-custom-code-to-the-project"></a>So fügen Sie dem Projekt benutzerdefinierten Code hinzu  
  
1.  Benennen Sie im Projektmappen-Explorer die Quelldatei <legacyBold>Window1.xaml</legacyBold> in <legacyBold>L2XDBForm.xaml</legacyBold> um. Die abhängige Quelldatei <legacyBold>Window1.xaml.cs</legacyBold> sollte automatisch in <legacyBold>L2XDBForm.xaml.cs</legacyBold> umbenannt werden.  
  
2.  Ersetzen Sie den Quellcode in der Datei „L2XDBForm.xaml“ durch den Codeabschnitt aus dem Thema [L2DBForm.xaml-Quellcode](../designers/l2dbform-xaml-source-code.md). (Verwenden Sie zum Arbeiten mit dieser Datei die XAML-Quellansicht.)  
  
3.  Ersetzen Sie den Quellcode in der Datei „L2XDBForm.xaml.cs“ durch den Codeabschnitt aus dem Thema [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md).  
  
4.  Ersetzen Sie in der Datei <legacyBold>App.xaml</legacyBold> alle Vorkommen der Zeichenfolge <legacyBold>Window1.xaml</legacyBold> durch <legacyBold>L2XDBForm.xaml</legacyBold>.  
  
5.  Erstellen Sie die Projektmappe, indem Sie **STRG+UMSCHALT+B** drücken.  
  
## <a name="running-the-program"></a>Ausführen des Programms  
 Das <legacyBold>LinqToXmlDataBinding</legacyBold>-Programm ermöglicht es dem Benutzer, eine Liste von Büchern anzuzeigen und zu bearbeiten, die als eingebettetes XML-Element gespeichert ist.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>So führen Sie das Programm aus und zeigen die Buchliste an  
  
1.  Führen Sie LinqToXmlDataBinding aus, indem Sie **F5** (**Debuggen starten**) oder **STRG+F5** (**Starten ohne Debuggen**) drücken. Daraufhin sollte ein Programmfenster mit dem Titel **Beispiel für die WPF-Datenbindung mit LINQ to XML** angezeigt werden.  
  
2.  Achten Sie auf den obersten Abschnitt der Benutzeroberfläche. Dort wird das unformatierte **XML** angezeigt, das die Buchliste darstellt. Die Anzeige erfolgt unter Verwendung eines WPF-<xref:System.Windows.Controls.TextBlock>-Steuerelements, das keine Interaktion mithilfe von Maus oder Tastatur zulässt.  
  
3.  Im zweiten vertikalen Abschnitt mit der Bezeichnung **Book List** (Buchliste) werden die Bücher als geordnete Nur-Text-Liste angezeigt. Dazu wird ein <xref:System.Windows.Controls.ListBox>-Steuerelement verwendet, das die Auswahl über Maus oder Tastatur zulässt.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>So fügen Sie der Liste Bücher hinzu und löschen Bücher daraus  
  
1.  Wenn Sie ein vorhandenes Buch aus der Liste löschen möchten, wählen Sie es im Abschnitt **Book List** aus, und klicken Sie dann auf die Schaltfläche **Remove Selected Book**. Der Bucheintrag wird daraufhin sowohl aus der Buchliste als auch aus der unformatierten XML-Quellauflistung entfernt.  
  
2.  Wenn Sie der Liste ein neues Buch hinzufügen möchten, geben Sie in die <xref:System.Windows.Controls.TextBox>-Steuerelemente **ID** und **Value** im letzten Abschnitt, **Add New Book**, Werte ein, und klicken Sie dann auf **Add Book**. Das Buch wird sowohl der Buchliste als auch der XML-Auflistung angefügt. Das Programm prüft die Eingabewerte nicht auf ihre Gültigkeit.  
  
#### <a name="to-edit-an-existing-book-entry"></a>So bearbeiten Sie einen vorhandenen Bucheintrag  
  
1.  Wählen Sie den Bucheintrag im zweiten Abschnitt, **Book List**, aus. Die aktuellen Werte des Bucheintrags sollten im dritten Abschnitt, **Edit Selected Book** (Ausgewähltes Buch bearbeiten), angezeigt werden.  
  
2.  Bearbeiten Sie die Werte mit der Tastatur. Sobald Sie zu einem anderen <xref:System.Windows.Controls.TextBox>-Steuerelement wechseln, werden die Änderungen automatisch in die XML-Auflistung und in die Buchliste übernommen.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiel](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Anwendungsentwicklung in Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)



