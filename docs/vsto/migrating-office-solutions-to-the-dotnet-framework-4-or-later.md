---
title: Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 729fafd1f6dfdf889293c9686f455be8de5a81fc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643716"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher
  Wenn das Zielframework eines Office-Projekts, um geändert wird die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder später von einer früheren Version von .NET Framework, einige zusätzliche Schritte möglicherweise erforderlich, um anzugeben, dass die Lösung auf Entwicklungs- und Endbenutzer-Computern ausgeführt. Weitere Informationen finden Sie unter [auf erforderliche Änderungen für das Ausführen von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Darüber hinaus wird das Projekt möglicherweise nicht mehr kompiliert. Einige Funktionen von Office-Projekten verfügen über unterschiedliche Programmiermodelle für die verschiedenen Versionen von .NET Framework. Wenn das Zielframework eines Office-Projekts von einer früheren .NET Framework-Version auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die folgenden Codeänderungen am Projekt vornehmen:

- [Aktualisieren von Excel- und Word-Projekte, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualisieren von Anpassungen von Menübändern in Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)

- [Aktualisieren von Formularbereichen in Outlook-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Das Zielframework eines Office-Projekts ändert sich, wenn Sie dieses Projekt von einer früheren Visual Studio-Version aktualisieren. Weitere Informationen finden Sie unter [aktualisieren und Migrieren von Office-Projektmappen](../vsto/upgrading-and-migrating-office-solutions.md).

  Weitere Informationen dazu, warum einige Funktionen in Office-Projekten haben ein anderes Programmiermodell, wenn Sie als Ziel der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher finden Sie unter [Änderungen am Entwurf von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5abzielen.](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) und [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Siehe auch
- [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)
- [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [Behandeln von Fehlern in Office-Projektmappen](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md)
