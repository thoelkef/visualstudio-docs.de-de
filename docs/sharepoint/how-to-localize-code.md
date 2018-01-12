---
title: 'Vorgehensweise: Lokalisieren von Code | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95c029a7a90283314bdded2a6beeb7f023d7e827
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-localize-code"></a>Gewusst wie: Lokalisieren von Code
  In nicht lokalisiertem Code werden hartcodierte Zeichenfolgenwerte verwendet. Zum Lokalisieren der Codezeichenfolgen werden diese durch Aufrufe von <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> ersetzt – einer Methode zum Verweisen auf lokalisierte Ressourcen.  
  
## <a name="localizing-code"></a>Lokalisieren von Code  
  
#### <a name="to-localize-code"></a>So lokalisieren Sie Code  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für ein Projekt, und wählen Sie dann **hinzufügen**, **Modul**.  
  
     Wählen Sie die **Ressourcendatei** Vorlage.  
  
    > [!NOTE]  
    >  Fügen Sie die Ressourcendatei einem SharePoint-Projektelement hinzu, damit die Eigenschaft "Bereitstellungstyp" verfügbar ist. Diese Eigenschaft ist später in dieser Prozedur erforderlich.  
  
2.  Benennen Sie die Ressourcendatei für die Standardsprache mit einem beliebigen Namen, und versehen Sie diesen mit der Erweiterung ".resx" (also beispielsweise "MyAppResources.resx").  
  
3.  Wiederholen Sie die Schritte 1 und 2, um dem SharePoint-Projektelement separate Ressourcendateien hinzuzufügen: jeweils eine für jede lokalisierte Sprache.  
  
     Verwenden Sie für jede lokalisierte Ressourcendatei den gleichen Basisnamen, aber fügen Sie jeweils die Kultur-ID hinzu. Benennen Sie also beispielsweise eine für Deutsch lokalisierte Ressource mit "MyAppResources.de-DE.resx".  
  
4.  Öffnen Sie die einzelnen Ressourcendateien, und fügen Sie ihnen lokalisierte Zeichenfolgen hinzu. Verwenden Sie in jeder Datei die gleichen Zeichenfolgen-IDs.  
  
5.  Ändern Sie den Wert, der die **Bereitstellungstyp** Eigenschaft der einzelnen Ressourcendateien auf **AppGlobalResource** für jede Datei auf den Ordner "App_GlobalResources" des Servers bereitstellen.  
  
6.  Lassen Sie den Wert, der die **Buildvorgang** Eigenschaft der einzelnen Dateien **eingebettete Ressource**.  
  
     Eingebettete Ressourcen werden in die DLL des Projekts kompiliert.  
  
7.  Erstellen Sie das Projekt, um die Satelliten-DLLs für die Ressource zu erstellen.  
  
8.  In der **Paket-Designer**, wählen Sie die **erweitert** Registerkarte, und fügen Sie die Satellitenassembly hinzu.  
  
9. In der **Speicherort** Feld, das einen Kultur-ID-Ordner, den Pfad zum Speicherort, z. B. de-DE voranstellen\\*Name des Projektelements*. resources.dll.  
  
10. Sofern von der Lösung nicht bereits auf die Assembly "System.Web" verwiesen wird, fügen Sie einen entsprechenden Verweis hinzu, und fügen Sie im Code eine Direktive zu <xref:System.Web> ein.  
  
11. Suchen Sie im Code nach allen hartcodierten Zeichenfolgen, die Benutzern angezeigt werden, z. B. Benutzeroberflächentexte, Fehler und Meldungstexte. Ersetzen Sie diese durch einen Aufruf der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>-Methode mit der folgenden Syntax:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Drücken Sie die F5-TASTE, um die Anwendung zu erstellen und auszuführen.  
  
13. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Vorgehensweise: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Vorgehensweise: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)  
  
  