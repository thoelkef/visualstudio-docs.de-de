---
title: "Gew&#228;hren von Vertrauensw&#252;rdigkeit f&#252;r Dokumente | Microsoft Docs"
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
  - "Gewähren von Vertrauenswürdigkeit [Office-Entwicklung in Visual Studio]"
  - "Aufnahmelisten [Office-Entwicklung in Visual Studio], Informationen zu Aufnahmelisten"
  - "Sicherheit [Office-Entwicklung in Visual Studio], Vertrauenswürdigkeit"
  - "Vertrauenswürdigkeit [Office-Entwicklung in Visual Studio], 2007 Office System"
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Gew&#228;hren von Vertrauensw&#252;rdigkeit f&#252;r Dokumente
  Ein Projekt auf Dokumentebene verfügt über die gleichen Sicherheitsanforderungen wie Projekte auf Anwendungsebene: Signieren der Manifeste mit einem Zertifikat oder durch Klicken auf die vertrauenswürdige Eingabeaufforderung.  Darüber hinaus muss sich das Dokument oder die Arbeitsmappe in einem Verzeichnis befinden, das als vertrauenswürdiger Speicherort festgelegt ist.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Vertrauenswürdige Speicherorte  
 Anwendungen in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und Office 2010 verfügen über Trust Centers, in denen Benutzer Sicherheits\- und Datenschutzeinstellungen, wie beispielsweise vertrauenswürdige Speicherorte, konfigurieren können.  Bei Office\-Projektmappen wird der lokale Computer als vertrauenswürdiger Speicherort eingestuft. Aufgrund des höheren Risikos gibt es bestimmte Verzeichnisse, die niemals als vertrauenswürdig eingestuft werden, z. B. die temporären Ordner für das System, für jeden Benutzer und für Internet Explorer.  
  
 Weitere Informationen über das Trust Center finden Sie unter [Sicherheitsrichtlinien und Einstellungen in Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202).  Weitere Informationen zum Erstellen, Verwalten, Entfernen und Konfigurieren von vertrauenswürdigen Ordnern finden Sie unter [Planen von Einstellungen für vertrauenswürdige Speicherorte und vertrauenswürdige Herausgeber in 2007 Office System](http://go.microsoft.com/fwlink/?LinkId=89203) und [Erstellen, Entfernen oder Ändern eines vertrauenswürdigen Speicherorts für Ihre Dateien](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## Überlegungen zur Sicherheit von Office\-Projektmappen  
 Es gibt mehrere Sicherheitsaspekte, wenn man überlegt, welche Ordner den vertrauenswürdigen Speicherorten hinzugefügt werden sollen:  
  
-   Lokale Ordner werden als sicherer und implizit vertrauenswürdig betrachtet.  Remotespeicherorte, wie beispielsweise Dateifreigaben, müssen als vertrauenswürdige Speicherorte festgelegt werden.  
  
-   Wenn Sie den vertrauenswürdigen Speicherorten ein Verzeichnis hinzufügen, wird auf diese Weise nicht nur den Office\-Projektmappen, sondern auch dem VBA\- und ActiveX\-Code die volle Vertrauenswürdigkeit gewährt.  Aus diesem Grund dürfen das Stammverzeichnis und die Ordner "Eigene Dateien" nicht als vertrauenswürdig festgelegt werden.  
  
-   Obwohl das Dokument selbst durch die Verwendung der vertrauenswürdigen Speicherorte vertrauenswürdig ist, sind zusätzliche Berechtigungen erforderlich, damit die Anpassung als vertrauenswürdig eingestuft wird.  Sie können der Anpassung volle Vertrauenswürdigkeit gewähren, indem Sie das Signieren der Manifeste mit einem Zertifikat verwenden, durch Klicken auf die vertrauenswürdige Eingabeaufforderung oder durch Installieren der Office\-Projektmappe im Verzeichnis "Programme".  
  
-   Sie können das Dokument oder die Arbeitsmappe einer Projektmappe auf Dokumentebene im selben Verzeichnis wie die Assembly oder in einem anderen Verzeichnis speichern.  Beispielsweise könnte sich das Dokument auf einem SharePoint\-Server befinden, und die Assembly könnte auf einer Dateifreigabe im Netzwerk vorhanden sein.  Weitere Informationen finden Sie unter [Gewusst wie: Veröffentlichen einer Office\-Projektmappe auf Dokumentebene auf einem SharePoint Server mit ClickOnce](http://msdn.microsoft.com/de-de/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## Siehe auch  
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Problembehandlung bei Office-Projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  