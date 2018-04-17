---
title: Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 830dcdb9e42472aa712c86ddb117b3b8003ac4d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migrieren von Office-Projektmappen in .NET Framework 4 oder höher
  Wenn das Zielframework eines Office-Projekts von einer früheren .NET Framework-Version in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, können einige zusätzliche Schritte erforderlich sein, damit die Projektmappe weiterhin auf Entwicklungs- und Endbenutzercomputern ausgeführt werden kann. Weitere Informationen finden Sie unter [Änderungen erforderlich sind, führen Sie Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Darüber hinaus wird das Projekt möglicherweise nicht mehr kompiliert. Einige Funktionen von Office-Projekten verfügen über unterschiedliche Programmiermodelle für die verschiedenen Versionen von .NET Framework. Wenn das Zielframework eines Office-Projekts von einer früheren .NET Framework-Version auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die folgenden Codeänderungen am Projekt vornehmen:  
  
-   [Aktualisieren von Excel- und Word-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Menübändern in Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Formularbereichen in Outlook-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Das Zielframework eines Office-Projekts ändert sich, wenn Sie dieses Projekt von einer früheren Visual Studio-Version aktualisieren. Weitere Informationen finden Sie unter [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Für Weitere Informationen dazu, warum einige Funktionen in Office-Projekten ein anderes Programmiermodell aufweisen, wenn Sie als Ziel der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher finden Sie in [Änderungen am Entwurf von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5abzielen](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) und [Visual Studio-Tools für Office-Laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Gewusst wie: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Beheben von Fehlern in Office-Projektmappen](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Zusätzliche Unterstützung bei Fehlern in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  