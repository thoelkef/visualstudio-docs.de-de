---
title: "Gewusst wie: Lokalisieren von Code | Microsoft Docs"
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
  - "Lokalisieren von Code [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Lokalisieren"
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Lokalisieren von Code
  In nicht lokalisiertem Code werden hartcodierte Zeichenfolgenwerte verwendet.  Zum Lokalisieren der Codezeichenfolgen werden diese durch Aufrufe von <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> ersetzt – einer Methode zum Verweisen auf lokalisierte Ressourcen.  
  
## Lokalisieren von Code  
  
#### So lokalisieren Sie Code  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für ein Projektelement, und wählen Sie anschließend **Hinzufügen** und dann **Modul** aus.  
  
     Wählen Sie die Vorlage **Ressourcendatei** aus.  
  
    > [!NOTE]  
    >  Fügen Sie die Ressourcendatei einem SharePoint\-Projektelement hinzu, damit die Eigenschaft "Bereitstellungstyp" verfügbar ist.  Diese Eigenschaft ist später in dieser Prozedur erforderlich.  
  
2.  Benennen Sie die Ressourcendatei für die Standardsprache mit einem beliebigen Namen, und versehen Sie diesen mit der Erweiterung ".resx" \(also beispielsweise "MyAppResources.resx"\).  
  
3.  Wiederholen Sie die Schritte 1 und 2, um dem SharePoint\-Projektelement separate Ressourcendateien hinzuzufügen: jeweils eine für jede lokalisierte Sprache.  
  
     Verwenden Sie für jede lokalisierte Ressourcendatei den gleichen Basisnamen, aber fügen Sie jeweils die Kultur\-ID hinzu.  Benennen Sie also beispielsweise eine für Deutsch lokalisierte Ressource mit "MyAppResources.de\-DE.resx".  
  
4.  Öffnen Sie die einzelnen Ressourcendateien, und fügen Sie ihnen lokalisierte Zeichenfolgen hinzu.  Verwenden Sie in jeder Datei die gleichen Zeichenfolgen\-IDs.  
  
5.  Ändern Sie den Wert der Eigenschaft **Bereitstellungstyp** der einzelnen Ressourcendateien zu **AppGlobalResource**, damit die Bereitstellung für jede Datei im Ordner "App\_GlobalResources" des Servers erfolgt.  
  
6.  Belassen Sie den Wert der Eigenschaft **Buildaktion** der einzelnen Dateien auf **Eingebettete Ressource**.  
  
     Eingebettete Ressourcen werden in die DLL des Projekts kompiliert.  
  
7.  Erstellen Sie das Projekt, um die Satelliten\-DLLs für die Ressource zu erstellen.  
  
8.  Wählen Sie im **Paket\-Designer** die Registerkarte **Erweitert** aus, und fügen Sie anschließend die Satellitenassembly hinzu.  
  
9. Stellen Sie dem Pfad zum Speicherort im Feld **Speicherort** einen Kultur\-ID\-Ordner voran \(beispielsweise "de\-DE\\*Project Item Name*.resources.dll"\).  
  
10. Sofern von der Lösung nicht bereits auf die Assembly "System.Web" verwiesen wird, fügen Sie einen entsprechenden Verweis hinzu, und fügen Sie im Code eine Direktive zu <xref:System.Web> ein.  
  
11. Suchen Sie im Code nach allen hartcodierten Zeichenfolgen, die Benutzern angezeigt werden, z. B. Benutzeroberflächentexte, Fehler und Meldungstexte.  Ersetzen Sie diese durch einen Aufruf der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>\-Methode mit der folgenden Syntax:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Drücken Sie die F5\-TASTE, um die Anwendung zu erstellen und auszuführen.  
  
13. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt.  Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint\-Server ein Language Pack installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## Siehe auch  
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Gewusst wie: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Gewusst wie: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Gewusst wie: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)  
  
  