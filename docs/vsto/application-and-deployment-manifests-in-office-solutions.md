---
title: "Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen | Microsoft Docs"
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
  - "Manifeste [Office-Entwicklung in Visual Studio]"
  - "Bereitstellungsmanifeste [Office-Entwicklung in Visual Studio]"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio]"
  - "Assemblys [Office-Entwicklung in Visual Studio], Aktualisieren"
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen
  Ein Anwendungsmanifest ist eine XML\-Datei, über die Informationen bereitgestellt werden, mit denen eine Office\-Projektmappe nach ihren Assemblys sucht und diese aktualisiert. Ein Anwendungsmanifest kann zusammen mit einem Bereitstellungsmanifest verwendet werden. Dabei handelt es sich um eine XML\-Datei, die auf dem Server gespeichert ist und die Informationen bereitstellt, die zum Auffinden der aktuellsten Version des Anwendungsmanifests und der Assemblys verwendet werden.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Manifeststruktur für Office\-Projektmappen  
 Für Microsoft Office\-Projektmappen, die mit den Office\-Entwicklungstools in Visual Studio erstellt wurden, basieren alle Manifeste auf dem standardmäßigen ClickOnce\-Schema. Beim Bereitstellen von Office\-Projektmappen befinden sich die Anwendungsmanifeste sowohl für Projekte auf Dokumentebene als auch für VSTO\-Add\-In\-Projekte im ClickOnce\-Cache. Die Bereitstellungsmanifeste werden nicht auf den Clientcomputer kopiert.  
  
 Informationen zum Inhalt von Anwendungs\- und Bereitstellungsmanifesten für Office\-Projekte finden Sie unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md) und [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md).  
  
## Erstellen von Anwendungs\- und Bereitstellungsmanifesten  
 Anwendungsmanifeste werden automatisch als Teil des Buildprozesses erstellt. Bei jeder Erstellung eines Projekts auf Dokumentebene wird der Speicherort des Bereitstellungsmanifests als benutzerdefinierte Dokumenteigenschaft in das Dokument eingebettet. Für VSTO\-Add\-Ins wird der Speicherort des Bereitstellungsmanifests in der Registrierung gespeichert.  
  
 Weitere Informationen zum **Webpublishing\-Assistenten** finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Weitere Informationen zur Funktionsweise von Manifesten mit Office\-Projektmappen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)  
  
  