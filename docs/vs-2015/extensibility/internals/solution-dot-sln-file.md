---
title: Projektmappen (. Sln)-Datei | Microsoft-Dokumentation
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
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001754"
---
# <a name="solution-sln-file"></a>Projektmappendatei (SLN)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Lösung ist eine Struktur zum Organisieren von Projekten in Visual Studio. Die Lösung verwaltet die Statusinformationen für Projekte in sln (textbasierten, shared) und SUO (binär, benutzerspezifischen Projektmappenoptionen)-Dateien. Weitere Informationen zu SUO-Dateien finden Sie unter [Benutzeroptionen bei Projektmappen (. Suo)-Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Wenn das VSPackage geladen wird, als Ergebnis in der SLN-Datei verwiesen wird, wird die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> , die in der SLN-Datei gelesen.  
  
 Die SLN-Datei enthält Informationen, die die Umgebung verwendet wird, suchen und laden die Name-Wert-Parameter für die beibehaltenen Daten und das Projekt VSPackages, die sie verweist. Wenn ein Benutzer eine Projektmappe geöffnet wird, die Umgebung durchläuft die `preSolution`, `Project`, und `postSolution` Informationen in der SLN-Datei zum Laden der Projektmappe, Projekte, in der Projektmappe, und dauerhaft gespeicherten Informationen angefügt wird, mit der Lösung.  
  
 Jedes Projekt die Datei enthält zusätzliche Informationen, die von der Umgebung zum Auffüllen der Hierarchie des Projekts Elemente lesen. Durch das Projekt wird der Datenpersistenz Hierarchie gesteuert wird. die Daten ist normalerweise nicht in der SLN-Datei gespeichert, obwohl absichtlich Projektinformationen zur sln-Datei schreiben können, wenn Sie dazu auf. Weitere Informationen in Bezug auf Dauerhaftigkeit finden Sie unter [Projektpersistenz](../../extensibility/internals/project-persistence.md) und [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Inhalt der Projektmappe-Datei  
 Die SLN-Datei besteht aus Abschnitten wie im folgenden Code dargestellt.  
  
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
  
 Um eine Lösung zu laden, führt die Umgebung die folgende Sequenz von Aufgaben.  
  
1. Die Umgebung den globalen Abschnitt der SLN-Datei liest und verarbeitet Sie alle Abschnitte, die markiert `preSolution`. In diesem Fall besteht eine solche Anweisung zur Verfügung:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Wenn die Umgebung liest die `GlobalSection('name')` -Tag, ordnet es den Namen für ein VSPackage mithilfe der Registrierung. Der Name des Schlüssels sollte vorhanden sein, in der Registrierung unter [HKLM\\< Application ID Registrierungsstamm\>\SolutionPersistence\AggregateGUIDs]. Der Standardwert ist die Paket-GUID (REG_SZ) des VSPackage, die die Einträge geschrieben hat.  
  
2. Die Umgebung, lädt das VSPackage, Aufrufe `QueryInterface` für das VSPackage für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> -Schnittstelle ab und ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> Methode mit den Daten in den Abschnitt aus, damit das VSPackage die Daten speichern kann. Dieser Prozess wird von die Umgebung für die einzelnen wiederholt `preSolution` Abschnitt.  
  
3. Die Umgebung durchläuft die persistenten Blöcken Projekt ab. In diesem Fall ist ein Projekt.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Diese Anweisung enthält die eindeutige Projekt-GUID und die GUID des Projekttyps. Diese Informationen werden von der Umgebung verwendet, um die Projektdatei oder Dateien aus der die Lösung suchen, und das VSPackage, die für jedes Projekt erforderlich sind. Das Projekt, die GUID wird an <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> um bestimmte VSPackage im Zusammenhang mit der das Projekt zu laden, klicken Sie dann das Projekt vom VSPackage geladen wird. In diesem Fall ist das VSPackage, die für dieses Projekt geladen wird, Visual Basic.  
  
    Jedes Projekt kann eine eindeutige Projekt-Instanz-ID beibehalten wird, damit es von anderen Projekten in der Projektmappe nach Bedarf aufgerufen werden kann. Wenn die Projektmappe und Projekte unter quellcodeverwaltung sind, sollte der Pfad zum Projekt im Idealfall relativ zum Pfad der Projektmappe sein. Wenn die Lösung zuerst geladen wird, darf nicht die Projektdateien auf dem Computer des Benutzers sein. Wenn Sie die Projektdatei, die auf dem Server relativ zu der Projektmappendatei gespeichert, ist es relativ einfach, für die Projektdatei wurde gefunden und auf dem Computer des Benutzers kopiert werden. Anschließend kopiert und lädt den Rest der Dateien für das Projekt erforderlich sind.  
  
4. Basierend auf den Informationen im Abschnitt "Projekt" der SLN-Datei enthalten sind, lädt die Umgebung jeder Projektdatei. Klicken Sie dann dient das Projekt selbst zum Auffüllen der Projekthierarchie, und laden alle geschachtelten Projekte zur Verfügung.  
  
5. Nachdem alle Abschnitte der SLN-Datei verarbeitet werden, wird die Lösung wird im Projektmappen-Explorer angezeigt und ist für die Änderungen durch den Benutzer bereit.  
  
   Wenn alle VSPackage, das ein Projekt in der Lösung implementiert ein Fehler auftritt, zu laden, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> Methode wird aufgerufen, und jedes andere Projekt in der Projektmappe ist die Möglichkeit erhält, Änderungen zu ignorieren, haben sie möglicherweise während des Ladens vorgenommen. Wenn Analyse Fehler auftreten, so viele Informationen wie möglich mit den Projektmappendateien beibehalten, und die Umgebung zeigt ein Dialogfeld, das dem Benutzer darauf hinzuweisen, dass die Lösung ist beschädigt.  
  
   Wenn die Lösung gespeichert oder geschlossen ist, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Methode wird aufgerufen, und übergeben Sie in der Hierarchie, um festzustellen, ob Änderungen vorgenommen haben, um die Projektmappe, die in der SLN-Datei eingegeben werden müssen. Ein null-Wert, der an übergebene `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, gibt an, dass die Informationen für die Projektmappe gespeichert werden sollte. Wenn der Wert nicht null ist, wird die dauerhaft gespeicherten Informationen für ein bestimmtes Projekt, das bestimmt, indem der Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle.  
  
   Wenn Informationen gespeichert werden, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle aufgerufen wird, mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> Methode. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Methode wird dann aufgerufen, von der Umgebung zum Abrufen von Name-Wert-Paare aus `IPropertyBag` Schnittstelle, und Schreiben der Informationen in die SLN-Datei.  
  
   `SaveSolutionProps` und `WriteSolutionProps` Objekte rekursiv aufgerufen werden, von der Umgebung zum Abrufen von Informationen gespeichert werden, aus der `IPropertyBag` Schnittstelle, bis alle Änderungen in der SLN-Datei vorgenommen wurden. Auf diese Weise können Sie sicherstellen, dass die Informationen mit der Lösung und zur Verfügung beim nächsten der Projektmappe öffnen beibehalten werden.  
  
   Alle geladenen VSPackages wird aufgelistet, um festzustellen, ob hat nichts in die SLN-Datei zu speichern. Es ist nur zur Ladezeit, die die Registrierungsschlüssel abgefragt werden. Die Umgebung weiß über alle geladenen Pakete, da sie in den Arbeitsspeicher zum Zeitpunkt sind die Projektmappe gespeichert wird.  
  
   Nur die SLN-Datei Einträge in enthält die `preSolution` und `postSolution` Abschnitte. In der SUO-Datei sind keine ähnliche Abschnitte, da die Lösung diese Informationen zum Laden von datenanforderungen. Die SUO-Datei enthält die benutzerspezifischen Optionen, z. B. private Anmerkungen, die, die nicht freigegeben oder unter quellcodeverwaltung gestellt werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Benutzeroptionen bei Projektmappen (. Suo)-Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Projektmappen](../../extensibility/internals/solutions-overview.md)
