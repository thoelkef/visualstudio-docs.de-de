---
title: "How to: Create File Associations For a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "file associations, ClickOnce applications"
  - "ClickOnce deployment, file associations"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create File Associations For a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen können eine oder mehrere Dateinamenerweiterungen zugeordnet werden, damit Anwendungen automatisch gestartet werden, wenn eine Datei des entsprechenden Typs geöffnet wird.  Die Unterstützung für eine Dateinamenerweiterung lässt sich einfach zu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen hinzufügen.  
  
### So erstellen Sie Dateizuordnungen für eine ClickOnce\-Anwendung  
  
1.  Erstellen Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung wie gewohnt, oder verwenden Sie die bestehende [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  
  
2.  Öffnen Sie das Anwendungsmanifest mit einem Text\- oder XML\-Editor, z. B. Windows Editor.  
  
3.  Suchen Sie das `assembly`\-Element.  Weitere Informationen hierzu finden Sie unter [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
4.  Fügen Sie ein `fileAssociation`\-Element als untergeordnetes Element des `assembly`\-Elements hinzu.  Das `fileAssociation`\-Element weist vier Attribute auf:  
  
    -   `extension`: Die der Anwendung zuzuordnende Dateinamenerweiterung.  
  
    -   `description`: Eine Beschreibung des Dateityps, die in der Windows\-Shell angezeigt wird.  
  
    -   `progid`: Eine Zeichenfolge, die den Dateityp eindeutig identifiziert, um diesen in der Registrierung zu markieren.  
  
    -   `defaultIcon`: Ein Symbol für den Dateityp.  Das Symbol muss im Anwendungsmanifest als Dateiressource hinzugefügt werden.  Weitere Informationen finden Sie unter [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Ein Beispiel für das `file`\- Element und das `fileAssociation`\-Element finden Sie unter [\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Wenn Sie der Anwendung mehr als einen Dateityp zuordnen möchten, fügen Sie zusätzliche `fileAssociation`\-Elemente hinzu.  Beachten Sie, dass für jeden Dateityp ein abweichendes `progid`\-Attribut verwendet werden muss.  
  
6.  Signieren Sie das Anwendungsmanifest erneut, sobald Sie das Manifest abschließend bearbeitet haben.  Hierzu können Sie Mage.exe in der Befehlszeile ausführen.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Weitere Informationen finden Sie unter [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)  
  
## Siehe auch  
 [\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)