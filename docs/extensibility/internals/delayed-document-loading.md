---
title: "Verz&#246;gertes Laden von Dokument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Verz&#246;gertes Laden von Dokument
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn ein Benutzer eine Visual Studio\-Projektmappe dargestellt, werden die meisten der zugehörigen Dokumente nicht sofort geladen werden. Fensterrahmen Dokument in einem ausstehenden Initialisierung Zustand erstellt wird, und ein Platzhalterdokument \(einen Stub\-Frame genannt\) wird in der ausführen\-Document\-Tabelle \(RDT\) platziert.  
  
 Die Erweiterung möglicherweise Projektdokumente, unnötigerweise geladen werden, indem Sie Elemente in die Dokumente Abfragen, bevor sie geladen werden. Dies kann der gesamte Speicherplatzbedarf für Visual Studio erhöhen.  
  
## Dokument laden  
 Die Stub\-Frame und das Dokument sind vollständig initialisiert, wenn der Benutzer durch Auswählen der Registerkarte des Fensterrahmens z. B. das Dokument zugreift. Das Dokument kann auch von einer Erweiterung initialisiert werden, die die Daten des Dokuments, den Zugriff auf die RDT direkt, um die Daten zu erhalten, oder den Zugriff auf die RDT indirekt durch eine der folgenden Aufrufe anfordert:  
  
-   Der Fensterrahmen show\-Methode: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Der Fensterrahmen GetProperty\-Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> auf die folgenden Eigenschaften:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Wenn die Erweiterung verwalteten Code verwendet wird, rufen Sie nicht <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> wenn Sie sicher sind, das Dokument ist nicht in den Status der ausstehenden Initialisierung oder das Dokument vollständig initialisiert werden soll... Dies ist, da diese Methode gibt immer das Dokument ein Datenobjekt, erstellen ihn bei Bedarf. Stattdessen sollten Sie eine der Methoden für die IVsRunningDocumentTable4\-Schnittstelle aufrufen.  
  
 Wenn die Erweiterung C\+\+ verwendet, können Sie übergeben `null` für die Parameter nicht möchten.  
  
 Sie können unnötige Dokument laden vermeiden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie die relevanten Eigenschaften anfordern: Bevor Sie andere Eigenschaften anfordern.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Diese Methode gibt ein <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> \-Objekt, das einen Wert für enthält <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> wenn das Dokument noch nicht initialisiert wurde.  
  
 Sie können feststellen, wenn ein Dokument geladen wurde, indem Sie abonnieren das RDT\-Ereignis, das ausgelöst wird, wenn ein Dokument vollständig initialisiert ist. Es gibt zwei Möglichkeiten:  
  
-   Wenn die Ereignissenke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   Andernfalls können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Im folgenden wird ein Szenario für einen hypothetischen Zugriff. Ein Visual Studio\-Erweiterung wünschen, um einige Informationen zu geöffneten Dokumente anzuzeigen, Anzahl und etwas über die Daten z. B. die Bearbeitung sperren. Es listet die Dokumente in der RDT mit <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> für jedes Dokument, um die bearbeiten Sperre Anzahl und den Dokument\-Daten abzurufen. Wenn das Dokument in den Status der ausstehenden Initialisierung ist, wird die Dokumentdaten anfordern unnötigerweise initialisiert werden.  
  
 Eine effizientere Möglichkeit besteht darin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> die Anzahl der Sperren bearbeiten und dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> zu bestimmen, ob das Dokument initialisiert wurde. Wenn nicht die Flags <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, das Dokument wurde bereits initialisiert, und fordern Sie die Daten mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nicht dazu, dass keine unnötige Initialisierung. Wenn die Flags enthalten <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, die Erweiterung sollte vermieden, dass die Daten erst, wenn das Dokument initialisiert wird. Dies kann im Ereignishandler OnAfterAttributeChange\(Ex\) erkannt werden.  
  
## Testen von Erweiterungen, um festzustellen, ob sie erzwingen, dass die Initialisierung  
 Es gibt keinen visuellen Hinweis an, ob ein Dokument initialisiert wurde, sodass es schwierig sein kann, um festzustellen, ob die Erweiterung Initialisierung erzwingt. Sie können einen Registrierungsschlüssel, die Überprüfung erleichtert festlegen, da den Titel jedes Dokuments verursacht werden, der um den Text nicht vollständig initialisiert `[Stub]` im Titel.  
  
 In **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, legen **StubTabTitleFormatString** auf **{0} \[Stub\]**.