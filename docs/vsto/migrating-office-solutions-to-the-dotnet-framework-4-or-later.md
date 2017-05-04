---
title: "Migrieren von Office-Projektmappen in .NET Framework&#160;4 oder h&#246;her | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Migrieren zu .NET Framework 4"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Migrieren von Office-Projektmappen in .NET Framework&#160;4 oder h&#246;her
  Wenn das Zielframework eines Office\-Projekts von einer früheren .NET Framework\-Version in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, können einige zusätzliche Schritte erforderlich sein, damit die Projektmappe weiterhin auf Entwicklungs\- und Endbenutzercomputern ausgeführt werden kann. Weitere Informationen finden Sie unter [Erforderliche Änderungen zum Ausführen von Office-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Darüber hinaus wird das Projekt möglicherweise nicht mehr kompiliert. Einige Funktionen von Office\-Projekten verfügen über unterschiedliche Programmiermodelle für die verschiedenen Versionen von .NET Framework. Wenn das Zielframework eines Office\-Projekts von einer früheren .NET Framework\-Version auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die folgenden Codeänderungen am Projekt vornehmen:  
  
-   [Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren der Anpassungen von Menübändern in Office-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Formularbereichen in Outlook-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Das Zielframework eines Office\-Projekts ändert sich, wenn Sie dieses Projekt von einer früheren Visual Studio\-Version aktualisieren. Weitere Informationen finden Sie unter [Aktualisieren und Migrieren von Office-Projektmappen](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Weitere Informationen dazu, warum einige Features in einem Office\-Projekt ein anderes Programmiermodell haben, wenn Sie das Projekt für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher vorsehen, finden Sie unter [Änderungen am Entwurf von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 abzielen](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) und [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Siehe auch  
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Gewusst wie: .NET Framework-Version als Ziel](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Problembehandlung in Office-Projektmappen](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  