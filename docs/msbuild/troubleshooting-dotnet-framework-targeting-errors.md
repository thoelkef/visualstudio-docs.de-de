---
title: Problembehandlung bei .NET Framework-Zielversionsfehlern | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 465952fa41eab7d112ca839be2940cded3d69b33
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744623"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Problembehandlung bei .NET Framework-Zielversionsfehlern
Dieses Thema beschreibt MSBuild-Fehler, die aufgrund von Verweisproblemen auftreten könnten, und wie Sie diese Fehler auflösen können.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Sie haben auf ein Projekt oder eine Assembly verwiesen, das bzw. die auf eine andere Version von .NET Framework abzielt
 Sie können Anwendungen erstellen, die auf Projekte oder Assemblys, die verschiedene Versionen von .NET Framework als Ziel verweisen. Beispielsweise können Sie eine Anwendung erstellen, die Das Clientprofil für .NET Framework 4 abzielt, aber verweist auf eine Assembly, die auf .NET Framework 2.0 abzielt. Wenn Sie ein Projekt, die auf eine frühere Version von .NET Framework abzielt erstellen, können nicht Sie jedoch festlegen einen Verweis in diesem Projekt auf ein Projekt oder eine Assembly, die auf Das Clientprofil für .NET Framework 4 oder .NET Framework 4 selbst abzielt. Um den Fehler aufzulösen, stellen Sie sicher, dass die Anwendung auf ein Profil oder Profile abzielt, die mit dem Profil kompatibel sind, auf die die Projekte oder Assemblys abzielen, auf die Ihre Anwendung verweist.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen
 Wenn Sie die Zielversion von .NET Framework für Ihre Anwendung ändern, ändert Visual Studio einige Verweise, aber Sie müssen möglicherweise einige Verweise manuell aktualisieren. Beispielsweise kann eine der oben erwähnten Fehler auftreten, wenn Sie die Zielanwendung Ändern der [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] und die Anwendung verfügt über Ressourcen oder Einstellungen, die für .NET Framework 4 Clientprofile verwenden.

 Um die Anwendungseinstellungen zu umgehen, öffnen Sie den **Projektmappen-Explorer**, wählen Sie **Alle Dateien anzeigen**, und bearbeiten Sie dann die Datei *app.config* im XML-Editor von Visual Studio. Ändern Sie die Version in den Einstellungen auf die entsprechende Version von .NET Framework. Beispielsweise können Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0 ändern. Öffnen Sie auf ähnliche Weise für eine Anwendung, der Ressourcen hinzugefügt wurden, den **Projektmappen-Explorer**, wählen Sie die Schaltfläche **Alle Dateien anzeigen**, erweitern Sie **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), und bearbeiten Sie dann die Datei *Resources.resx* im XML-Editor von Visual Studio. Ändern Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0.

 Wenn die Anwendung über Ressourcen wie Symbole oder Bitmaps oder Einstellungen wie Datenverbindungs-Zeichenfolgen verfügt, können Sie die Fehler auch auflösen, indem Sie alle Elemente auf der Seite **Einstellungen** auf der **Projekt-Designers** entfernen und dann die erforderlichen Einstellungen erneut hinzufügen.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen, und die Verweise werden nicht aufgelöst
 Wenn Sie ein Projekt auf eine andere Version von .NET Framework neu zuweisen, können die Verweise nicht ordnungsgemäß in einigen Fällen aufgelöst werden. Explizite vollqualifizierte Verweise auf Assemblys führen häufig zu diesem Problem, jedoch können Sie es auflösen, indem Sie die Verweise entfernen, die nicht aufgelöst werden, und dann wieder dem Projekt hinzufügen. Als Alternative können Sie die Projektdatei bearbeiten, um die Verweise zu ersetzen. Zunächst entfernen Sie Verweise in folgender Form:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Dann ersetzen Sie sie durch die einfache Form:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Nach Schließen und erneutem Öffnen des Projekts sollten Sie es auch neu erstellen, um sicherzustellen, dass alle Verweise ordnungsgemäß aufgelöst werden.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)
- [Übersicht über .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)