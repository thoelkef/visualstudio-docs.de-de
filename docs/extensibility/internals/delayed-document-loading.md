---
title: Verzögertes Laden von Dokument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc10d7807633433b38fa8587d41c2ac3c0273ebe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="delayed-document-loading"></a>Verzögertes Laden von Dokument
Wenn ein Benutzer eine Visual Studio-Projektmappe erneut öffnet, werden die meisten der zugehörigen Dokumente nicht sofort geladen werden. Die dokumentfensterrahmen in einem ausstehenden Initialisierung Zustand erstellt wird, und ein Platzhalterdokument (einen Stub-Frame genannt) wird in der Ausführung-Dokument-Tabelle (RDT) platziert.  
  
 Die Erweiterung kann dazu führen, dass Projektdokumente unnötigerweise geladen werden, indem Sie Elemente in die Dokumente Abfragen, bevor sie geladen werden. Dies kann die gesamte Speicherverwendung für Visual Studio verbessern.  
  
## <a name="document-loading"></a>Dokument laden  
 Der Stub-Frame und dem Dokument werden vollständig initialisiert, wenn der Benutzer das Dokument z. B. zugreift durch Auswählen der Registerkarte des Fensterrahmens. Das Dokument kann von einer Erweiterung, die das Dokument, entweder durch den Zugriff auf die RDT direkt, um die Daten abzurufen oder den Zugriff auf die RDT indirekt durch eine der folgenden Aufrufe datenanforderungen initialisiert werden:  
  
-   Der Fensterrahmen show-Methode: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Der Fensterrahmen GetProperty-Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> auf die folgenden Eigenschaften:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Wenn die Erweiterung verwalteten Code verwendet wird, sollten Sie nicht aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , außer Sie sicher, dass sind das Dokument ist nicht im Status "Ausstehende Initialisierung" oder das Dokument vollständig initialisiert werden soll... Dies ist, da diese Methode immer das Dokument gibt Datenobjekt, erstellen ihn bei Bedarf. Stattdessen sollten Sie eine der Methoden für die IVsRunningDocumentTable4-Schnittstelle aufrufen.  
  
 Wenn die Erweiterung C++ verwendet wird, können Sie übergeben `null` für die Parameter, die Sie nicht möchten.  
  
 Sie können unnötige Dokument laden vermeiden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie die relevanten Eigenschaften anfordern: Bevor Sie andere Eigenschaften anfordern.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> Diese Methode gibt ein <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> -Objekt, das einen Wert für enthält <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , wenn das Dokument noch nicht initialisiert wurde.  
  
 Sie können feststellen, wenn ein Dokument geladen wurde, durch Abonnieren des RDT-Ereignisses, das ausgelöst wird, wenn ein Dokument vollständig initialisiert wurde. Es gibt zwei Möglichkeiten:  
  
-   Wenn die Ereignissenke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   Andernfalls können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Im folgenden wird das Szenario für eine hypothetische Dokument. Eines Visual Studio, der Erweiterung einige Informationen über geöffnete Dokumente angezeigt werden soll, z. B. die Bearbeitung gesperrt werden Anzahl und etwas über die Dokumentdaten. Es listet die Dokumente in der RDT mit <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> für jedes Dokument, um die Daten für das Sperren Bearbeiten der Anzahl und Dokument abzurufen. Wenn das Dokument im Status "Ausstehende Initialisierung" ist, bewirkt, dass die Dokumentdaten anfordern unnötigerweise initialisiert werden.  
  
 Eine effizientere Methode dafür Dies ist die Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> zum Abrufen der Anzahl der Sperren bearbeiten, und klicken Sie dann verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> zu bestimmen, ob das Dokument initialisiert wurde. Wenn Sie nicht die Flags enthalten <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, das Dokument wurde bereits initialisiert wurde, und zum Anfordern der Dokumentdaten mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nicht dazu, dass keine unnötige Initialisierung. Wenn die Flags enthalten <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, die Erweiterung sollte vermieden, dass die Daten bis zur Initialisierung des Dokuments. Dadurch kann im Ereignishandler OnAfterAttributeChange(Ex) erkannt werden.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testen von Erweiterungen, um festzustellen, ob sie erzwingen, dass die Initialisierung  
 Es gibt keinen sichtbaren Hinweis an, ob ein Dokument initialisiert wurde, sodass es schwierig sein kann, um festzustellen, ob die Erweiterung Initialisierung erzwungen wird. Sie können einen Registrierungsschlüssel, die Überprüfung erleichtert festlegen, den Titel des jedes Dokument verursacht werden, die um den Text nicht vollständig initialisiert ist `[Stub]` im Titel.  
  
 In **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**legen **StubTabTitleFormatString** auf **{0} [Stub]**.