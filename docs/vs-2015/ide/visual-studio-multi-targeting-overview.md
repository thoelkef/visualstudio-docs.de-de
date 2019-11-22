---
title: Übersicht über die Ausrichtung auf mehrere Zielversionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a816981b41dd8ca2a2119bbd99c776c6a7e2436
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296888"
---
# <a name="visual-studio-multi-targeting-overview"></a>Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] können Sie die Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] angeben, die für die Anwendung erforderlich ist. Wenn Sie diese Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden möchten, um die Entwicklung eines Projekts fortzusetzen, das Sie in einer früheren Version begonnen haben, müssen Sie das Frameworkziel nicht ändern. Sie können auch eine Projektmappe mit Projekten erstellen, die andere Versionen des Frameworks als Ziel verwenden. Durch Frameworkziele wird gewährleistet, dass die Anwendung nur Funktionen verwendet, die in der angegebenen Version des Frameworks verfügbar sind.

> [!TIP]
> Sie können auch Anwendungen für unterschiedliche Plattformen als Ziel verwenden. Weitere Informationen finden Sie unter [Multitargeting (Festlegen von Zielversionen)](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Frameworkzielfunktionen
 Frameworkziele umfassen folgende Funktionen:

- Wenn Sie ein Projekt öffnen, das eine frühere Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] als Ziel verwendet, kann [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] das Projekt automatisch aktualisieren oder das Ziel unverändert lassen.

- Wenn Sie ein Projekt erstellen, können Sie die gewünschte [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Zielversion angeben.

- Sie können die Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ändern, auf die ein vorhandenes Projekt abzielt.

- Sie können eine andere [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version als Zielversion für unterschiedliche Projekte in der gleichen Projektmappe festlegen.

- Wenn Sie die Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ändern, auf die ein Projekt ausgerichtet ist, werden in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] alle erforderlichen Änderungen an Verweisen und Konfigurationsdateien vorgenommen.

  Visual Studio kann dynamisch Änderungen in der Entwicklungsumgebung vornehmen, wenn Sie mit einem Projekt arbeiten, das eine frühere [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version als Ziel hat. Dazu zählen u. a. folgende Aktionen:

- Filtern von Elementen in den Dialogfeldern **Neues Projekt**, **Neues Element hinzufügen**, **Neuen Verweis hinzufügen** und **Dienstverweis hinzufügen**, um die Optionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von benutzerdefinierten Steuerelementen in der **Toolbox**, um die Steuerelemente zu entfernen, die in der Zielversion nicht verfügbar sind, und um nur die neuesten Steuerelemente anzuzeigen, wenn mehrere Steuerelemente für die Zielversion verfügbar sind.

- Filtern von IntelliSense, um Sprachfunktionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von Eigenschaften im Fenster **Eigenschaften**, um die Eigenschaften auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von Menüoptionen, um Optionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Für Builds werden die Version des Compilers und die Compileroptionen verwendet, die für die Zielversion geeignet sind.

> [!NOTE]
> Durch Frameworkziele wird nicht garantiert, dass die Anwendung ordnungsgemäß ausgeführt wird. Sie müssen die Anwendung dennoch testen, um sicherzustellen, dass Sie mit der Zielversion ausgeführt wird. Sie können keine Frameworkversionen als Ziel verwenden, die älter als .NET Framework 2.0 sind.

## <a name="selecting-a-target-framework-version"></a>Auswählen einer Zielframeworkversion
 Wenn Sie ein Projekt erstellen, wählen Sie die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Zielversion im Dialogfeld **Neues Projekt** aus. Die Liste der verfügbaren Projektvorlagen wird basierend auf der Auswahl gefiltert. Für ein vorhandenes Projekt können Sie die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Zielversion über das Dialogfeld „Projekteigenschaften“ ändern. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
> In den Express-Editionen von Visual Studio können Sie das Zielframework im Dialogfeld **Neues Projekt** nicht festlegen.

## <a name="resolving-system-and-user-assembly-references"></a>Auflösen von System- und Benutzerassemblyverweisen
 Um eine .NET Framework-Version als Ziel zu verwenden, müssen Sie zunächst die entsprechenden Assemblyverweise installieren. Assemblyverweise für die .NET Framework-Versionen 2.0, 3.0 und 3.5 sind in der Version .NET Framework 3.5 SP1 enthalten, die Sie von der Website [Microsoft Download Center, Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) herunterladen können. Assemblyverweise für .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile und Silverlight sind auch auf der Website [Visual Studio-Downloads](https://go.microsoft.com/fwlink/?LinkId=179687) verfügbar.

> [!NOTE]
> Ein .NET Framework Client Profile ist eine Teilmenge von .NET Framework, das einen eingeschränkten Satz von Bibliotheken und Funktionen bereitstellt. Weitere Informationen finden Sie unter [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 Über das Dialogfeld **Verweis hinzufügen[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] werden Systemassemblys deaktiviert, die nicht zur** -Zielversion gehören, sodass sie nicht versehentlich zu einem Projekt hinzugefügt werden können. (Systemassemblys sind DLL-Dateien, die in einer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version enthalten sind.) Verweise, die zu einer .NET Framework-Version gehören, die älter ist als die Zielversion, werden nicht aufgelöst, und Steuerelemente, die von einem solchen Verweis abhängen, können nicht hinzugefügt werden. Wenn Sie einen solchen Verweis aktivieren möchten, setzen Sie das [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Ziel des Projekts auf eine Version zurück, die den Verweis enthält.  Weitere Informationen finden Sie unter [Einführung in den Projekt-Designer](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Weitere Informationen zu Assemblyverweisen finden Sie unter [Resolving Assemblies at Design Time (Auflösen von Assemblys zur Entwurfszeit)](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Aktivieren von LINQ
 Wenn Sie .NET Framework 3.5 oder eine höhere Version als Ziel verwenden, werden automatisch ein Verweis auf "System.Core" und ein Import auf Projektebene für "System.Linq" (nur in Visual Basic) hinzugefügt. Wenn Sie LINQ-Features verwenden möchten, müssen Sie zusätzlich Option Infer aktivieren (nur in Visual Basic). Der Verweis und der Import werden automatisch entfernt, wenn Sie die Zielversion auf eine frühere .NET Framework-Version ändern. Weitere Informationen finden Sie unter [How to: Create a LINQ Project (Vorgehensweise: Erstellen eines LINQ-Projekts)](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Siehe auch
[Festlegung von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)
[.NET Framework Multi-Targeting for ASP.NET Web Projects](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) (Festlegung von Zielversionen für .NET Framework für ASP.NET-Web-Projekte) 
[Platform compatibility and system requirements](/visualstudio/productinfo/vs2015-compatibility-vs) (Plattformkompatibilität und Systemanforderungen)
