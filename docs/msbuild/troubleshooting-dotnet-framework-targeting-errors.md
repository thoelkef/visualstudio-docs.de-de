---
title: Problembehandlung bei .NET Framework-Zielversionsfehlern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6376abc29f6f06541b9cd7f3d181b97ab7b38e5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Problembehandlung bei .NET Framework-Zielversionsfehlern
Dieses Thema beschreibt MSBuild-Fehler, die aufgrund von Verweisproblemen auftreten könnten, und wie Sie diese Fehler auflösen können.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Sie haben auf ein Projekt oder eine Assembly verwiesen, das bzw. die auf eine andere Version von .NET Framework abzielt  
 Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf eine andere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] abzielen. Beispielsweise können Sie eine Anwendung erstellen, die auf das Clientprofil für [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] abzielt, aber auf eine Assembly verweist, die auf .NET Framework 2.0 ausgerichtet ist. Wenn Sie jedoch ein Projekt erstellen, das auf eine frühere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] abzielt, können Sie keinen Verweis in diesem Projekt auf ein Projekt oder eine Assembly festlegen, die auf das Clientprofil für [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] selbst abzielt. Um den Fehler aufzulösen, stellen Sie sicher, dass die Anwendung auf ein Profil oder Profile abzielt, die mit dem Profil kompatibel sind, auf die die Projekte oder Assemblys abzielen, auf die Ihre Anwendung verweist.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen  
 Wenn Sie die Zielversion von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] für Ihre Anwendung ändern, ändert Visual Studio einige Verweise, aber Sie müssen möglicherweise einige Verweise manuell aktualisieren. Einer der oben erwähnten Fehler könnte z.B. auftreten, wenn Sie eine Anwendung so ändern, dass sie auf [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] abzielt, und diese Anwendung verfügt über Ressourcen oder Einstellungen, die vom Clientprofil für [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] abhängen.  
  
 Um die Anwendungseinstellungen zu umgehen, öffnen Sie den **Projektmappen-Explorer**, wählen Sie **Alle Dateien anzeigen**, und bearbeiten Sie dann die Datei „app.config“ im XML-Editor von Visual Studio. Ändern Sie die Version in den Einstellungen auf die entsprechende Version von .NET Framework. Beispielsweise können Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0 ändern. Öffnen Sie auf ähnliche Weise für eine Anwendung, der Ressourcen hinzugefügt wurden, den **Projektmappen-Explorer**, wählen Sie die Schaltfläche **Alle Dateien anzeigen**, erweitern Sie **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), und bearbeiten Sie dann die Datei „Resources.resx“ im XML-Editor von Visual Studio. Ändern Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0.  
  
 Wenn die Anwendung über Ressourcen wie Symbole oder Bitmaps oder Einstellungen wie Datenverbindungs-Zeichenfolgen verfügt, können Sie die Fehler auch auflösen, indem Sie alle Elemente auf der Seite **Einstellungen** auf der **Projekt-Designers** entfernen und dann die erforderlichen Einstellungen erneut hinzufügen.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen, und die Verweise werden nicht aufgelöst  
 Wenn Sie ein Projekt einer anderen Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] neu zuweisen, werden die Verweise in einigen Fällen vielleicht nicht korrekt aufgelöst. Explizite vollqualifizierte Verweise auf Assemblys führen häufig zu diesem Problem, jedoch können Sie es auflösen, indem Sie die Verweise entfernen, die nicht aufgelöst werden, und dann wieder dem Projekt hinzufügen. Als Alternative können Sie die Projektdatei bearbeiten, um die Verweise zu ersetzen. Zunächst entfernen Sie Verweise in folgender Form:  
  
```xml  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Dann ersetzen Sie sie durch die einfache Form:  
  
```xml  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Nach Schließen und erneutem Öffnen des Projekts sollten Sie es auch neu erstellen, um sicherzustellen, dass alle Verweise ordnungsgemäß aufgelöst werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)   
 [Festlegen einer bestimmten .NET-Framework-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)