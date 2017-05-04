---
title: "Gewusst wie: Lokalisieren einer Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Funktionen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Lokalisieren"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Lokalisieren einer Funktion
  Standardmäßig werden für Funktionstitel und \-beschreibungen hartcodierte Zeichenfolgenwerte verwendet.  Zum Lokalisieren des Funktionstitels und der Beschreibung werden die Zeichenfolgen durch Ausdrücke ersetzt, die auf die lokalisierten Ressourcen verweisen.  
  
## Lokalisieren einer Funktion  
  
#### So lokalisieren Sie eine Funktion  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Knoten **Feature1**, und wählen Sie dann **Funktionsressource hinzufügen** aus.  
  
2.  Im Dialogfeld **Ressource hinzufügen** wählen Sie in der Liste als Kultur für die Standardsprachefunktionsressourcendatei **Invariante Sprache** aus.  
  
3.  Wiederholen Sie den vorherigen Schritt für jede lokalisierte Sprache und Sprachen Ihrer Wahl für die lokalisierten Funktionsressourcendateien auswählen.  
  
     Separate Funktionsressourcendateien werden erstellt: eine für die Standardsprache und jeweils eine für jede lokalisierte Sprache, die Sie unterstützen möchten.  
  
4.  Öffnen Sie die einzelnen Ressourcendateien im Ressourcen\-Editor, und geben Sie dann alle Zeichenfolgen\-IDs und ihre Werte ein.  
  
     In der Standardfunktionsressourcendatei, geben eine Zeichenfolgen\-ID des Titels mit einem Wert von Mein Funktions\-Titels und eine ID der zweiten Zeichenfolge der Beschreibung mit dem Wert " mit ein.  Verwenden Sie für jede lokalisierte Ressourcendatei die gleichen Zeichenfolgen\-IDs, die in der Standardfunktionsressource verwendet werden, aber geben Sie lokalisierte Zeichenfolgen für die Werte ein.  
  
5.  Nach allen Ressourcenwerte eingeben, öffnen Sie das Kontextmenü für die Funktion \(beispielsweise "Feature1.feature"\), und wählen Sie dann **Ansicht\-Designer**, um die Funktion im Funktions\-Designer zu öffnen.  
  
6.  Um die Felder **Titel** und **Beschreibung** in der Funktion zu suchen, verwenden Sie das folgende Format um Werte in den Feldern ein:  
  
     `$Resources:` *String ID*  
  
     Geben Sie im Feld **Funktionstitel** beispielsweise "$Resources:Title" und im Feld **Funktionsbeschreibung** beispielsweise "$Resources:Description" ein.  
  
     Die Zeichenfolgen\-IDs müssen die übereinstimmen, die in Ressourcendateien verwendet werden.  
  
7.  Drücken Sie die F5\-TASTE, um die Anwendung zu erstellen und auszuführen.  
  
8.  Öffnen Sie in SharePoint im Menü **Websiteaktionen**, **Websiteeinstellungen** auswählen, und dann, im Abschnitt **Websiteaktionen** Wählen Sie den Link **Websitefeatures verwalten** aus.  
  
9. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     Der lokalisierte Funktionstitel und die lokalisierte Beschreibung werden in der Anwendung angezeigt.  Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint\-Server ein Language Pack installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## Siehe auch  
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Gewusst wie: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Gewusst wie: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Gewusst wie: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)  
  
  