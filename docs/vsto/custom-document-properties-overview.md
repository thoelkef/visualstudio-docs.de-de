---
title: "&#220;bersicht &#252;ber benutzerdefinierte Dokumenteigenschaften | Microsoft Docs"
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
helpviewer_keywords: 
  - "_AssemblyLocation-Eigenschaft"
  - "_AssemblyName-Eigenschaft"
  - "Benutzerdefinierte Dokumenteigenschaften"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Benutzerdefinierte Eigenschaften"
  - "Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte Eigenschaften"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte Eigenschaften"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# &#220;bersicht &#252;ber benutzerdefinierte Dokumenteigenschaften
  Wenn Sie ein Projekt auf Dokumentebene erstellen, fügt Visual Studio dem Dokument zwei benutzerdefinierte Eigenschaften im Projekt hinzu: \_AssemblyLocation und \_AssemblyName.  Wenn ein Benutzer ein Dokument öffnet, sucht die Microsoft Office\-Anwendung nach diesen benutzerdefinierten Dokumenteigenschaften.  Wenn sie im Dokument vorhanden sind, lädt die Anwendung [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], die die Anpassung startet.  Weitere Informationen finden Sie unter [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 Diese Eigenschaft enthält die CLSID einer Schnittstelle in der Ladeprogrammkomponente der Office\-Lösung von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Der CLSID\-Wert ist 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B.  Sie sollten diesen Wert nie ändern.  
  
## \_AssemblyLocation  
 Diese Eigenschaft enthält eine Zeichenfolge, die Details über das Bereitstellungsmanifest zur Anpassung bereitstellt.  Weitere Informationen zu Manifesten finden Sie unter [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Der Wert der \_AssemblyLocation\-Eigenschaft kann abhängig von der Bereitstellung der Projektmappe unterschiedliche Formate besitzen:  
  
-   Wenn die Lösung für die Installation von einer Website, einem UNC\-Pfad oder einem CD\- oder USB\-Laufwerk veröffentlicht wird, besitzt die \_AssemblyLocation\-Eigenschaft das Format *DeploymentManifestPath*|*SolutionID*.  Die folgende Zeichenfolge ist ein Beispiel:  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   Wenn Sie die Lösung von Visual Studio aus ausführen oder debuggen, besitzt die \_AssemblyLocation\-Eigenschaft das Format *DeploymentManifestName*|*SolutionID*|vstolocal.  Die folgende Zeichenfolge ist ein Beispiel:  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 Die *SolutionID* ist eine GUID, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zum Identifizieren der Lösung verwendet.  *SolutionID* wird automatisch generiert, wenn Sie das Projekt erstellen. Der **vstolocal** Begriff zu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gibt an, dass die Assembly im gleichen Ordner wie das Dokument geladen werden soll.  
  
## Siehe auch  
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Gewusst wie: Veröffentlichen einer Office\-Projektmappe mit ClickOnce](http://msdn.microsoft.com/de-de/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  