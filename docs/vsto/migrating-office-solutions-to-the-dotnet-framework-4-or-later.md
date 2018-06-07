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
ms.openlocfilehash: 7ac244bebb1a625c7858a62399ee79126e309cf2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571798"
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher
  Wenn das Zielframework eines Office-Projekts von einer früheren .NET Framework-Version in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, können einige zusätzliche Schritte erforderlich sein, damit die Projektmappe weiterhin auf Entwicklungs- und Endbenutzercomputern ausgeführt werden kann. Weitere Informationen finden Sie unter [erforderten Änderungen zum Ausführen von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Darüber hinaus wird das Projekt möglicherweise nicht mehr kompiliert. Einige Funktionen von Office-Projekten verfügen über unterschiedliche Programmiermodelle für die verschiedenen Versionen von .NET Framework. Wenn das Zielframework eines Office-Projekts von einer früheren .NET Framework-Version auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die folgenden Codeänderungen am Projekt vornehmen:  
  
-   [Aktualisieren von Excel- und Word-Projekte, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Menübändern in Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Formularbereichen in Outlook-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Das Zielframework eines Office-Projekts ändert sich, wenn Sie dieses Projekt von einer früheren Visual Studio-Version aktualisieren. Weitere Informationen finden Sie unter [aktualisieren und Migrieren von Office-Projektmappen](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Für Weitere Informationen dazu, warum einige Funktionen in Office-Projekten ein anderes Programmiermodell aufweisen, wenn Sie als Ziel der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher finden Sie in [Änderungen am Entwurf von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5abzielen](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) und [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Vorgehensweise: eine Version von .NET Framework als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Problembehandlung von Fehlern in Office-Projektmappen](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  