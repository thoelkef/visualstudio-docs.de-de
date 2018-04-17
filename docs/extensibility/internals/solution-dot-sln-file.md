---
title: Lösung (. Sln) Datei | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73d6f7fb83e9420f59122135761ce44ea641fe57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="solution-sln-file"></a>Lösung (. Sln)-Datei
Eine Lösung ist eine Struktur zum Organisieren von Projekten in Visual Studio. Die Lösung behält die Zustandsinformationen für Projekte in sln (textbasierten, freigegebenen) und .suo (binär, benutzerspezifische Projektmappenoptionen)-Dateien. Weitere Informationen zu SUO-Dateien finden Sie unter [-projektmappenbenutzeroptionen (. Suo) Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Wenn Ihr VSPackage geladen wird, als Ergebnis in der SLN-Datei verwiesen wird, ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> , in der SLN-Datei zu lesen.  
  
 Die SLN-Datei enthält die textbasierte Informationen, mit die Umgebung zu suchen und laden die Name-Wert-Parameter für die persistente Daten als auch das Projekt VSPackages, die darauf verweist. Wenn ein Benutzer eine Projektmappe geöffnet wird, die Umgebung durchläuft die `preSolution`, `Project`, und `postSolution` Informationen in der SLN-Datei zum Laden der Projektmappe Projekte innerhalb der Projektmappe und alle dauerhaft gespeicherten Informationen an die Lösung angefügt.  
  
 Jedes Projekt-Datei enthält zusätzliche Informationen, die von der Umgebung zum Auffüllen der Hierarchie mit Elementen des Projekts zu lesen. Die Hierarchie-Datenpersistenz wird vom Projekt gesteuert wird. die Daten werden normalerweise nicht in der SLN-Datei gespeichert, zwar absichtlich Projektinformationen in die SLN-Datei schreiben kann, wenn Sie dies auswählen. Weitere Informationen im Zusammenhang mit der Persistenz, finden Sie unter [Projektdauerhaftigkeit](../../extensibility/internals/project-persistence.md) und [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Dateiinhalte Lösung  
 Die SLN-Datei besteht aus mehreren Abschnitten wie im folgenden Code dargestellt.  
  
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
  
 Um eine Projektmappe zu laden, führt die Umgebung die folgende Sequenz von Aufgaben.  
  
1.  Die Umgebung den globalen Teil der SLN-Datei liest und verarbeitet alle Abschnitte markiert `preSolution`. In diesem Fall besteht eine solche Anweisung:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Wenn die Umgebung liest die `GlobalSection('name')` Tag, ordnet sie den Namen für ein VSPackage mit der Registrierung. Der Name des Schlüssels sollten vorhanden sein, in der Registrierung unter [HKLM\\< Application ID Registrierungsstamm\>\SolutionPersistence\AggregateGUIDs]. Standardwert für den Schlüssel wird die Paket-GUID (REG_SZ) das VSPackage, das die Einträge geschrieben hat.  
  
2.  Die Umgebung lädt das VSPackage, Aufrufe `QueryInterface` für das VSPackage für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> -Schnittstelle, und ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> Methode mit den Daten in den Abschnitt aus, damit VSPackages die Daten gespeichert werden kann. Die Umgebung wiederholt diesen Vorgang für jede `preSolution` Abschnitt.  
  
3.  Die Umgebung durchläuft die persistenten Blöcken Projekt ab. In diesem Fall besteht ein Projekt.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Diese Anweisung enthält die eindeutige Projekt-GUID und der Projekttyp GUID. Diese Informationen werden von der Umgebung verwendet, um die Projektdatei oder Dateien aus der die Lösung suchen, und das VSPackage, die für jedes Projekt erforderlich sind. Das Projekt GUID an <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> um bestimmte VSPackage im Zusammenhang mit dem Projekt zu laden, klicken Sie dann das Projekt vom VSPackage geladen wird. In diesem Fall ist das VSPackage, die für dieses Projekt geladen wird, Visual Basic.  
  
     Jedes Projekt kann eine eindeutige Instanz-ID beibehalten wird, damit darauf zugegriffen werden kann, je nach Bedarf vom andere Projekte in der Projektmappe. Im Idealfall sollte unter quellcodeverwaltung die Projektmappen und Projekte sind, der Pfad zum Projekt relativ zum Pfad der Projektmappe sein. Wenn die Lösung zuerst geladen wird, darf nicht die Projektdateien auf dem Computer des Benutzers sein. Durch die Verwendung der Projektdatei, die auf dem Server relativ zur Lösungsdatei gespeichert, ist es relativ einfach, für die Projektdatei gefunden und auf dem Computer des Benutzers kopiert werden. Anschließend kopiert und lädt den Rest der Dateien für das Projekt erforderlich sind.  
  
4.  Basierend auf den Informationen, die im Abschnitt "Projekt" die SLN-Datei enthalten sind, lädt die Umgebung jede Projektdatei aus. Das Projekt selbst ist verantwortlich für das Auffüllen der Projekthierarchie und laden alle geschachtelten Projekte.  
  
5.  Nachdem alle Abschnitte der SLN-Datei verarbeitet werden, wird die Projektmappe im Projektmappen-Explorer angezeigt, und ist für die Änderungen durch den Benutzer bereit.  
  
 Wenn alle VSPackage, das in der Projektmappe ein Projekt implementiert nicht geladen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> Methode wird aufgerufen, und alle anderen Projekts in der Projektmappe eine Möglichkeit, um Änderungen zu ignorieren, kann beim Laden von vorgenommenen, erhält. Wenn Analyse Fehler auftreten, werden so viele Informationen wie möglich mit der Lösungsdateien beibehalten und die Umgebung wird das Dialogfeld Warnung des Benutzers die Projektmappe ist beschädigt.  
  
 Wenn die Projektmappe gespeichert oder "geschlossen", die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Methode wird aufgerufen, und übergeben Sie in der Hierarchie, um festzustellen, ob Änderungen vorgenommen wurden, um die Projektmappe, die in der SLN-Datei eingegeben werden müssen. Einen null-Wert, der an übergebene `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, gibt an, dass die Informationen für die Projektmappe gespeichert werden sollte. Wenn der Wert nicht null ist, wird die dauerhaft gespeicherten Informationen für ein bestimmtes Projekt, ermittelt der Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle.  
  
 Wenn Informationen gespeichert werden sollen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle wird aufgerufen, mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> Methode. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> aufgerufen wird dann von der Umgebung zum Abrufen von Name / Wert-Paare aus `IPropertyBag` Schnittstelle, und Schreiben der Informationen in der SLN-Datei.  
  
 `SaveSolutionProps` und `WriteSolutionProps` Objekte rekursiv aufgerufen werden, von der Umgebung zum Abrufen von Informationen gespeichert werden, aus der `IPropertyBag` -Schnittstelle, bis alle Änderungen in der SLN-Datei eingegeben wurden. Auf diese Weise können Sie sicherstellen, dass die Informationen mit der Lösung und die verfügbaren beim nächsten der Projektmappe öffnen beibehalten wird.  
  
 Jedes geladene VSPackage wird aufgelistet, um festzustellen, ob alles sln-Datei zu speichern. Es ist nur zur Ladezeit, die die Registrierungsschlüssel abgefragt werden. Die Umgebung weiß über alle geladenen Pakete, da es im Speicher zum Zeitpunkt sind, in die Projektmappe gespeichert wird.  
  
 Nur die SLN-Datei Einträge in der `preSolution` und `postSolution` Abschnitte. In der SUO-Datei sind keine ähnliche Abschnitte, da die Lösung diese Informationen ordnungsgemäß Laden benötigt werden. Die SUO-Datei enthält benutzerspezifische-Optionen, z. B. private Notizen, die nicht freigegeben oder Quellcodeverwaltungssystem platziert werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Benutzeroptionen bei Projektmappen (. Suo)-Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Projektmappen](../../extensibility/internals/solutions.md)