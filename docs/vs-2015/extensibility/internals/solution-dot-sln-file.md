---
title: Lösung (. Sln)-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154963"
---
# <a name="solution-sln-file"></a>Projektmappendatei (SLN)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Lösung ist eine Struktur zum Organisieren von Projekten in Visual Studio. Die Lösung verwaltet die Zustandsinformationen für Projekte in SLN-Dateien (Text basiert, Shared) und suo (binäre, benutzerspezifische Projektmappenoptionen). Weitere Informationen zu suo-Dateien finden Sie unter [Solution User Options (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Wenn das VSPackage als Ergebnis eines referenzierten in der SLN-Datei geladen wird, ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> auf, um in der SLN-Datei zu lesen.  
  
 Die SLN-Datei enthält textbasierte Informationen, die die Umgebung verwendet, um die Name-Wert-Parameter für die persistenten Daten und die Projekt-VSPackages zu suchen und zu laden, auf die verwiesen wird. Wenn ein Benutzer eine Projekt Mappe öffnet, durchläuft die Umgebung `preSolution` die `Project` Informationen, und `postSolution` in der SLN-Datei, um die Projekt Mappe, die Projekte in der Projekt Mappe und alle beibehaltenen Informationen, die an die Lösung angefügt sind, zu laden.  
  
 Die Datei jedes Projekts enthält zusätzliche Informationen, die von der Umgebung gelesen werden, um die Hierarchie mit den Elementen dieses Projekts aufzufüllen. Die Daten Persistenz der Hierarchie wird vom Projekt gesteuert. die Daten werden normalerweise nicht in der SLN-Datei gespeichert, obwohl Sie die Projektinformationen absichtlich in die SLN-Datei schreiben können, wenn Sie sich dafür entscheiden. Weitere Informationen zur Persistenz finden Sie unter [Projekt Persistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Inhalt der Lösungs Datei  
 Die SLN-Datei besteht aus mehreren Abschnitten, wie im folgenden Code veranschaulicht.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Zum Laden einer Projekt Mappe führt die Umgebung die folgende Tasksequenz aus.  
  
1. Die Umgebung liest den globalen Abschnitt der SLN-Datei und verarbeitet alle markierten Abschnitte `preSolution` . In diesem Fall gibt es eine solche Anweisung:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Wenn die Umgebung das `GlobalSection('name')` Tag liest, ordnet Sie den Namen mithilfe der Registrierung einem VSPackage zu. Der Schlüssel Name muss in der Registrierung unter [HKLM \\<Application ID Registry root \> \solutionpersistence\aggregateguids] vorhanden sein. Der Standardwert der Schlüssel ist die Paket-GUID (REG_SZ) des VSPackage, das die Einträge geschrieben hat.  
  
2. Die Umgebung lädt das VSPackage, ruft das `QueryInterface` VSPackage für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Schnittstelle auf und ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> Methode mit den Daten im-Abschnitt auf, damit das VSPackage die Daten speichern kann. Die Umgebung wiederholt diesen Vorgang für jeden `preSolution` Abschnitt.  
  
3. Die Umgebung durchläuft die Projekt Beibehaltungs Blöcke. In diesem Fall ist ein Projekt vorhanden.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Diese Anweisung enthält die eindeutige Projekt-GUID und die Projekttyp-GUID. Diese Informationen werden von der Umgebung verwendet, um die Projektdateien zu suchen, die zur Projekt Mappe gehören, und das VSPackage, das für jedes Projekt erforderlich ist. Die Projekt-GUID wird an weitergegeben, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> um das spezifische VSPackage zu laden, das mit dem Projekt verknüpft ist, und das Projekt wird dann vom VSPackage geladen. In diesem Fall ist das VSPackage, das für dieses Projekt geladen wird, Visual Basic.  
  
    Jedes Projekt kann eine eindeutige Projekt Instanz-ID persistent speichern, damit auf Sie nach Bedarf von anderen Projekten in der Projekt Mappe zugegriffen werden kann. Wenn sich die Projekt Mappe und die Projekte unter Quell Code Verwaltung befinden, sollte der Pfad zum Projekt im Idealfall relativ zum Pfad der Projekt Mappe sein. Wenn die Projekt Mappe zum ersten Mal geladen wird, dürfen sich die Projektdateien nicht auf dem Computer des Benutzers befinden. Wenn die Projektdatei auf dem Server relativ zur Projektmappendatei gespeichert ist, ist es relativ einfach, die Projektdatei zu finden und auf den Computer des Benutzers zu kopieren. Anschließend werden die restlichen Dateien kopiert und geladen, die für das Projekt benötigt werden.  
  
4. Basierend auf den Informationen, die im Projektabschnitt der SLN-Datei enthalten sind, lädt die Umgebung jede Projektdatei. Das Projekt selbst ist dann dafür verantwortlich, die Projekt Hierarchie aufzufüllen und alle in der Tabelle befindlichen Projekte zu laden.  
  
5. Nachdem alle Abschnitte der SLN-Datei verarbeitet wurden, wird die Projekt Mappe in Projektmappen-Explorer angezeigt und kann vom Benutzer geändert werden.  
  
   Wenn ein VSPackage, das ein Projekt in der Projekt Mappe implementiert, nicht geladen werden kann, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> wird die-Methode aufgerufen, und jedes andere Projekt in der Projekt Mappe erhält die Möglichkeit, Änderungen zu ignorieren, die Sie möglicherweise beim Laden vorgenommen haben. Wenn Analyse-Fehler auftreten, werden so viele Informationen wie möglich in den Projektmappendateien beibehalten, und in der Umgebung wird ein Dialogfeld angezeigt, in dem der Benutzer darauf gewarnt wird, dass die Lösung beschädigt ist  
  
   Wenn die Projekt Mappe gespeichert oder geschlossen wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> wird die-Methode aufgerufen und an die-Hierarchie übergeben, um festzustellen, ob an der Projekt Mappe Änderungen vorgenommen wurden, die in die SLN-Datei eingegeben werden müssen. Ein NULL-Wert, der an in übermittelt wird, gibt an, `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> dass Informationen für die Lösung persistent gespeichert werden. Wenn der Wert nicht NULL ist, gelten die beibehaltenen Informationen für ein bestimmtes Projekt, das durch den Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle bestimmt wird.  
  
   Wenn Informationen gespeichert werden sollen, wird die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle mit einem Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> Methode aufgerufen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> -Methode wird dann von der Umgebung aufgerufen, um die Name-Wert-Paare aus der `IPropertyBag` Schnittstelle abzurufen und die Informationen in die SLN-Datei zu schreiben.  
  
   `SaveSolutionProps` -und- `WriteSolutionProps` Objekte werden rekursiv von der Umgebung aufgerufen, um Informationen abzurufen, die von der Schnittstelle gespeichert werden, `IPropertyBag` bis alle Änderungen in die SLN-Datei eingegeben wurden. Auf diese Weise können Sie sicherstellen, dass die Informationen mit der Lösung persistent gespeichert werden und beim nächsten Öffnen der Lösung verfügbar sind.  
  
   Jedes geladene VSPackage wird aufgezählt, um festzustellen, ob es Elemente enthält, die in der SLN-Datei gespeichert werden sollen. Es ist nur während der Ladezeit, dass die Registrierungsschlüssel abgefragt werden. Die Umgebung kennt alle geladenen Pakete, da Sie sich im Speicher befinden, wenn die Projekt Mappe gespeichert wird.  
  
   Nur die SLN-Datei enthält Einträge in den `preSolution` `postSolution` Abschnitten und. Die SUO-Datei enthält keine ähnlichen Abschnitte, da diese Informationen für die Lösung erforderlich sind, um ordnungsgemäß geladen zu werden. Die SUO-Datei enthält benutzerspezifische Optionen, z. b. private Notizen, die nicht für die Freigabe oder Platzierung in der Quell Code Verwaltung vorgesehen sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Projektmappenbenutzeroptionen (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Lösungen](../../extensibility/internals/solutions-overview.md)
