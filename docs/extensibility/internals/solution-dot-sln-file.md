---
title: Lösung (. Sln)-Datei
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705334"
---
# <a name="solution-sln-file"></a>Lösungsdatei (.sln)

Eine Projektmappe ist eine Struktur zum Organisieren von Projekten in Visual Studio. Die Projektmappe verwaltet die Statusinformationen für Projekte in zwei Dateien:

- .sln-Datei (textbasiert, freigegeben)

- .suo-Datei (binäre, benutzerspezifische Lösungsoptionen)

Weitere Informationen zu .suo-Dateien finden Sie unter [Lösungsbenutzeroptionen (. Suo) Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Wenn Ihr VSPackage als Ergebnis des Verweises in der .sln-Datei geladen wird, ruft die Umgebung auf, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> in der .sln-Datei zu lesen.

Die .sln-Datei enthält textbasierte Informationen, die die Umgebung verwendet, um die Namenswertparameter für die persistenten Daten und das Projekt VSPackages zu suchen und zu laden. Wenn ein Benutzer eine Projektmappe `preSolution`öffnet, durchläuft die Umgebung die , `Project`und `postSolution` Informationen in der .sln-Datei, um die Projektmappe, Projekte innerhalb der Projektmappe und alle an die Projektmappe zugeordneten Informationen zu laden.

Die Datei jedes Projekts enthält zusätzliche Informationen, die von der Umgebung gelesen werden, um die Hierarchie mit den Elementen dieses Projekts aufzufüllen. Die Hierarchiedatenpersistenz wird vom Projekt gesteuert. Die Daten werden normalerweise nicht in der .sln-Datei gespeichert, obwohl Sie absichtlich Projektinformationen in die .sln-Datei schreiben können, wenn Sie dies wünschen. Weitere Informationen zur Persistenz finden Sie unter [Projektpersistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Dateiheader

Der Header einer .sln-Datei sieht wie folgt aus:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definitionen

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardheader, der die Dateiformatversion definiert.

`# Visual Studio 15`\
Die Hauptversion von Visual Studio, die diese Projektmappendatei (zuletzt) gespeichert hat. Diese Informationen steuern die Versionsnummer im Lösungssymbol.

`VisualStudioVersion = 15.0.26730.15`\
Die Vollversion von Visual Studio, die die Projektmappendatei (zuletzt) gespeichert hat. Wenn die Projektmappendatei von einer neueren Version von Visual Studio mit derselben Hauptversion gespeichert wird, wird dieser Wert nicht aktualisiert, um die Abwanderung in Lösungsdateien zu mindern.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Die minimale (älteste) Version von Visual Studio, die diese Projektmappendatei öffnen kann.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definitionen

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardheader, der die Dateiformatversion definiert.

`# Visual Studio Version 16`\
Die Hauptversion von Visual Studio, die diese Projektmappendatei (zuletzt) gespeichert hat. Diese Informationen steuern die Versionsnummer im Lösungssymbol.

`VisualStudioVersion = 16.0.28701.123`\
Die Vollversion von Visual Studio, die die Projektmappendatei (zuletzt) gespeichert hat. Wenn die Projektmappendatei von einer neueren Version von Visual Studio mit derselben Hauptversion gespeichert wird, wird dieser Wert nicht aktualisiert, um die Abwanderung in der Datei zu mindern.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Die minimale (älteste) Version von Visual Studio, die diese Projektmappendatei öffnen kann.

::: moniker-end

## <a name="file-body"></a>Dateikörper

Der Text einer .sln-Datei besteht aus `GlobalSection`mehreren Abschnitten, die beschriftet sind, wie folgt:

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

Um eine Lösung zu laden, führt die Umgebung die folgende Abfolge von Aufgaben aus:

1. Die Umgebung liest den Abschnitt Global der .sln-Datei und verarbeitet alle markierten `preSolution`Abschnitte . In dieser Beispieldatei gibt es eine solche Anweisung:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Wenn die Umgebung `GlobalSection('name')` das Tag liest, ordnet sie den Namen einem VSPackage mithilfe der Registrierung zu. Der Schlüsselname sollte in der Registrierung\\ unter [HKLM<Application ID Registry Root\>'SolutionPersistence'AggregateGUIDs] vorhanden sein. Der Standardwert des Schlüssels ist die Paket-GUID (REG_SZ) des VSPackage, das die Einträge geschrieben hat.

2. Die Umgebung lädt das `QueryInterface` VSPackage, ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> das VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> für die Schnittstelle auf und ruft die Methode mit den Daten im Abschnitt auf, damit das VSPackage die Daten speichern kann. Die Umgebung wiederholt diesen `preSolution` Vorgang für jeden Abschnitt.

3. Die Umgebung durchforst die Persistenzblöcke des Projekts. In diesem Fall gibt es ein Projekt.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Diese Anweisung enthält die eindeutige Projekt-GUID und die Projekttyp-GUID. Diese Informationen werden von der Umgebung verwendet, um die Projektdatei oder die Dateien zu finden, die zur Projektmappe gehören, und das für jedes Projekt erforderliche VSPackage. Die Projekt-GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> wird übergeben, um das spezifische VSPackage im Zusammenhang mit dem Projekt zu laden, dann wird das Projekt vom VSPackage geladen. In diesem Fall ist das VSPackage, das für dieses Projekt geladen wird, Visual Basic.

   Jedes Projekt kann eine eindeutige Projektinstanz-ID beibehalten, sodass bei Bedarf von anderen Projekten in der Projektmappe darauf zugegriffen werden kann. Wenn sich die Projektmappe und die Projekte unter Quellcodeverwaltung befinden, sollte der Pfad zum Projekt im Vergleich zum Pfad zur Projektmappe relativ sein. Wenn die Projektmappe zum ersten Mal geladen wird, können sich die Projektdateien nicht auf dem Computer des Benutzers befinden. Wenn die Projektdatei relativ zur Projektmappendatei auf dem Server gespeichert ist, ist es relativ einfach, die Projektdatei zu finden und auf den Computer des Benutzers zu kopieren. Anschließend werden die restlichen Dateien kopiert und geladen, die für das Projekt benötigt werden.

4. Basierend auf den Informationen im Projektabschnitt der .sln-Datei lädt die Umgebung jede Projektdatei. Das Projekt selbst ist dann für das Auffüllen der Projekthierarchie und das Laden aller verschachtelten Projekte verantwortlich.

5. Nachdem alle Abschnitte der .sln-Datei verarbeitet wurden, wird die Projektmappe im Projektmappen-Explorer angezeigt und ist vom Benutzer zur Änderung bereit.

Wenn ein VSPackage, das ein Projekt in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> Projektmappe implementiert, nicht geladen werden kann, wird die Methode aufgerufen, und jedes andere Projekt in der Projektmappe erhält die Möglichkeit, Änderungen zu ignorieren, die während des Ladens möglicherweise vorgenommen wurden. Wenn Analysefehler auftreten, werden so viele Informationen wie möglich mit den Lösungsdateien beibehalten, und die Umgebung zeigt ein Dialogfeld an, in dem der Benutzer gewarnt wird, dass die Lösung beschädigt ist.

Wenn die Lösung gespeichert oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> geschlossen wird, wird die Methode aufgerufen und an die Hierarchie übergeben, um festzustellen, ob Änderungen an der Lösung vorgenommen wurden, die in die .sln-Datei eingegeben werden müssen. Ein NULL-Wert, `QuerySaveSolutionProps` der <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>an übergeben wird, gibt an, dass Informationen für die Lösung beibehalten werden. Wenn der Wert nicht null ist, werden die persistenten Informationen für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ein bestimmtes Projekt verwendet, das durch den Zeiger auf die Schnittstelle bestimmt wird.

Wenn Informationen gespeichert werden sollen, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> einem Zeiger auf die Methode aufgerufen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Methode wird dann von der Umgebung aufgerufen, `IPropertyBag` um die Name-Wert-Paare von der Schnittstelle abzurufen und die Informationen in die .sln-Datei zu schreiben.

`SaveSolutionProps`und `WriteSolutionProps` Objekte werden von der Umgebung rekursiv aufgerufen, um `IPropertyBag` Informationen abzurufen, die von der Schnittstelle gespeichert werden sollen, bis alle Änderungen in die .sln-Datei eingegeben wurden. Auf diese Weise können Sie sicherstellen, dass die Informationen mit der Lösung beibehalten werden und beim nächsten Öffnen der Lösung verfügbar sind.

Jedes geladene VSPackage wird aufgezählt, um zu sehen, ob es etwas in der .sln-Datei zu speichern hat. Nur zum Zeitpunkt des Ladens werden die Registrierungsschlüssel abgefragt. Die Umgebung kennt alle geladenen Pakete, da sie sich zum Zeitpunkt des Speicherns der Lösung im Arbeitsspeicher befinden.

Nur die .sln-Datei `preSolution` enthält `postSolution` Einträge in und Abschnitten. Es gibt keine ähnlichen Abschnitte in der .suo-Datei, da die Lösung diese Informationen benötigt, um ordnungsgemäß geladen zu werden. Die .suo-Datei enthält benutzerspezifische Optionen, z. B. private Notizen, die nicht freigegeben oder unter Quellcodeverwaltung platziert werden sollen.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Datei mit Benutzeroptionen in Projektmappen (SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Lösungen](../../extensibility/internals/solutions-overview.md)
