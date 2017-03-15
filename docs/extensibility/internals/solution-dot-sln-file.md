---
title: "L&#246;sung (. Sln)-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sln-Dateien, VSPackages"
  - "Lösungen, .sln-Dateien"
  - ".sln-Dateien, VSPackages"
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# L&#246;sung (. Sln)-Datei
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Lösung ist eine Struktur zum Organisieren von Projekten in Visual Studio. Die Lösung verwaltet den Zustand für Projekte in der sln \(Text\-basierte, freigegebener\) und SUO \(binär, benutzerspezifischen Lösungsoptionen\)\-Dateien. Weitere Informationen zu SUO\-Dateien finden Sie unter [Benutzeroptionen bei Projektmappen \(. Datei Suo\)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Wenn das VSPackage geladen wird, als Ergebnis in der SLN\-Datei verwiesen wird, ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> in der SLN\-Datei zu lesen.  
  
 Die SLN\-Datei enthält die Textinformationen, die die Umgebung verwendet wird, suchen und laden die Name\-Wert\-Parameter für die beibehaltenen Daten und das Projekt VSPackages darauf verweist. Wenn ein Benutzer eine Projektmappe geöffnet wird, die Umgebung, durchläuft die `preSolution`, `Project`, und `postSolution` Informationen in der SLN\-Datei zum Laden der Projektmappe Projekte innerhalb der Projektmappe, und alle beibehaltenen Informationen an der Lösung.  
  
 Jedes Projekt die Datei enthält zusätzliche Informationen, die von der Umgebung zum Auffüllen der Hierarchie mit diesem Projekt Elemente gelesen werden. Das Projekt wird die Hierarchie Datenpersistenz gesteuert wird. die Daten werden normalerweise nicht in der SLN\-Datei gespeichert, obwohl absichtlich Projektinformationen zur sln\-Datei schreiben können, wenn Sie dies auswählen. Weitere Informationen im Hinblick auf Dauerhaftigkeit finden Sie unter [Projekt\-Persistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## Inhalt der Projektmappen\-Datei  
 Die SLN\-Datei besteht aus mehreren Abschnitten wie im folgenden Code dargestellt.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}" EndProject Global GlobalSection(SolutionNotes) = postSolution EndGlobalSection GlobalSection(SolutionConfiguration) = preSolution ConfigName.0 = Debug ConfigName.1 = Release EndGlobalSection GlobalSection(ProjectDependencies) = postSolution EndGlobalSection GlobalSection(ProjectConfiguration) = postSolution {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86 {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86 {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86 {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86 EndGlobalSection GlobalSection(ExtensibilityGlobals) = postSolution EndGlobalSection GlobalSection(ExtensibilityAddIns) = postSolution EndGlobalSection EndGlobal  
```  
  
 Um eine Lösung zu laden, führt die Umgebung die folgende Sequenz von Aufgaben.  
  
1.  Die Umgebung globale Abschnitt der SLN\-Datei liest und verarbeitet alle Abschnitte markiert `preSolution`. In diesem Fall ist eine solche Anweisung vorhanden:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution ConfigName.0 = Debug ConfigName.1 = Release  
    ```  
  
     Wenn die Umgebung liest die `GlobalSection('name')` \-Tag, wird der Name ein VSPackage mit der Registrierung. Der Name des Schlüssels sollte in der Registrierung unter \[HKLM\\ \< ID Registrierung Anwendungsstamm \> \\SolutionPersistence\\AggregateGUIDs\] vorhanden sein. Die Schlüssel Wert ist die Paket\-GUID \(REG\_SZ\) VSPackages, die die Einträge geschrieben wurden.  
  
2.  Die Umgebung lädt das VSPackage Aufrufe `QueryInterface` auf das VSPackage für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> \-Schnittstelle ab und ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> Methode mit den Daten in den Abschnitt, damit das VSPackage Daten speichern kann. Die Umgebung wiederholt diesen Vorgang für jede `preSolution` Abschnitt.  
  
3.  Die Umgebung durchläuft die persistenten Blöcken Projekt. In diesem Fall ist ein Projekt.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}" EndProject  
    ```  
  
     Diese Anweisung enthält die eindeutige GUID\-Projekt und den Projekttyp\-GUID. Diese Informationen werden von der Umgebung verwendet, um die Dateien der Projektmappe oder Projektdatei finden, und das VSPackage für jedes Projekt erforderlich sind. Die GUID wird an Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> um bestimmte VSPackage im Zusammenhang mit dem Projekt zu laden, klicken Sie dann das Projekt geladen wird das VSPackage. In diesem Fall ist das VSPackage, die für dieses Projekt geladen wird, Visual Basic.  
  
     Jedes Projekt kann eine eindeutige Instanz\-ID beibehalten wird, damit sie von anderen Projekten in der Projektmappe nach Bedarf zugegriffen werden kann. Idealerweise sollte die Projektmappen und Projekte Quellcodeverwaltungssystem sind, der Pfad für das Projekt relativ zum Pfad der Projektmappe sein. Wenn die Lösung zuerst geladen wird, darf nicht die Projektdateien auf dem Computer des Benutzers sein. Da Sie die Projektdatei, die auf dem Server in Bezug auf die Projektmappendatei gespeichert, ist es relativ einfach, für die Projektdatei gefunden werden, auf dem Computer des Benutzers kopiert. Anschließend kopiert und lädt den Rest der für das Projekt erforderlichen Dateien.  
  
4.  Basierend auf den Informationen, die im Projektabschnitt "die SLN\-Datei enthalten sind, lädt die Umgebung jede Projektdatei aus. Das Projekt selbst ist dann verantwortlich für das Auffüllen der Projekthierarchie und laden alle geschachtelten Projekte.  
  
5.  Nachdem alle Abschnitte der SLN\-Datei verarbeitet werden, wird die Lösung wird im Projektmappen\-Explorer angezeigt und ist für die Änderung durch den Benutzer bereit.  
  
 Wenn alle VSPackage, die in der Projektmappe ein Projekt implementiert nicht geladen, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> wird aufgerufen, und jedes andere Projekt in der Projektmappe ist die Möglichkeit erhält, Änderungen zu ignorieren, sie während des Ladens vorgenommen haben. Wenn Analyse Fehler auftreten, so viele Informationen wie möglich mit den Projektmappendateien beibehalten, und die Umgebung zeigt ein Dialogfeld, das der Benutzer gewarnt wird, dass die Lösung beschädigt ist.  
  
 Wenn die Projektmappe gespeichert oder geschlossen ist, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> \-Methode aufgerufen und an der Hierarchie, um festzustellen, ob Änderungen vorgenommen wurden, um die Projektmappe, die in der SLN\-Datei eingegeben werden müssen. Ein null\-Wert übergeben `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, gibt an, dass die Informationen für die Lösung gespeichert werden sollte. Wenn der Wert nicht null ist, wird die dauerhaft gespeicherten Informationen für ein bestimmtes Projekt, ermittelt der Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle.  
  
 Wenn Informationen gespeichert werden, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle heißt mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> Methode. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Methode wird dann aufgerufen, von der Umgebung zum Abrufen des Name\-Wert\-Paare aus `IPropertyBag` Schnittstelle, und Schreiben der Informationen in der SLN\-Datei.  
  
 `SaveSolutionProps` und `WriteSolutionProps` Objekte rekursiv aufgerufen werden, von der Umgebung zum Abrufen von Informationen aus gespeichert werden die `IPropertyBag` Schnittstelle, bis alle Änderungen in der SLN\-Datei vorgenommen wurden. Auf diese Weise können Sie sicherstellen, dass die Informationen mit der Lösung und die verfügbaren beim nächsten der Projektmappe öffnen beibehalten wird.  
  
 Jedes geladene VSPackage ist aufgelistet, um festzustellen, ob alle Elemente in der SLN\-Datei zu speichern. Es ist nur beim Laden, die die Registrierungsschlüssel abgefragt werden. Die Umgebung kennt alle geladenen Pakete Speicher zum Zeitpunkt werden, wenn die Projektmappe gespeichert wird.  
  
 Nur die SLN\-Datei Einträge in enthält die `preSolution` und `postSolution` Abschnitte. In der SUO\-Datei sind keine ähnliche Abschnitte, da die Lösung dieser Informationen Laden benötigt werden. Die SUO\-Datei enthält benutzerspezifische Optionen, z. B. private Notizen, die nicht bestimmt werden, freigegeben oder Quellcodeverwaltungssystem platziert werden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Benutzeroptionen bei Projektmappen \(. Datei Suo\)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Projektmappen](../../extensibility/internals/solutions.md)