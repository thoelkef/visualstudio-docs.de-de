---
title: Verzögertes Laden von Dokumenten | Microsoft-Dokumentation
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
ms.openlocfilehash: 03ca02010586711fa1a9af463f2fde5d0f4963a5
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500367"
---
# <a name="delayed-document-loading"></a>Verzögertes Laden von Dokumenten
Wenn ein Benutzer mit Visual Studio-Projektmappe erneut öffnet, werden die meisten der zugehörigen Dokumente nicht sofort geladen werden. Die dokumentfensterrahmen wird in einem Zustand ausstehende Initialisierung erstellt, und ein Platzhalterdokument (einen Stub-Frame bezeichnet) befindet sich in der ausgeführten Dokumententabelle (RDT).  
  
Die Erweiterung möglicherweise Projektdokumente unnötigerweise geladen werden, durch Abfragen der Elemente in den Dokumenten, bevor sie geladen werden, die Gesamtspeicherbedarf für Visual Studio erhöhen können.  
  
## <a name="document-loading"></a>Laden von Dokumenten  
Dokument mit den Stub-Frames und sind vollständig initialisiert, wenn der Benutzer das Dokument, z. B. greift auf durch Auswählen der Registerkarte des Fensterrahmens. Das Dokument kann auch von einer Erweiterung initialisiert werden, die die Daten eines Dokuments, entweder durch den Zugriff auf den RDT direkt, um die Daten zu erhalten oder den Zugriff auf den RDT indirekt selbst eines der folgenden Aufrufe anfordert:  
  
- Der Fensterrahmen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode.  
  
- Der Fensterrahmen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode für die folgenden Eigenschaften:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
- Wenn Ihre Erweiterung verwalteten Code verwendet wird, sollten Sie nicht aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> es sei denn, Sie sicher, dass das Dokument ist nicht im Zustand "ausstehender-Initialization" oder das Dokument vollständig initialisiert werden soll. Der Grund ist, da die-Methode immer die Doc gibt-Datenobjekt, wodurch bei Bedarf erstellt. Sie sollten rufen Sie stattdessen eine der Methoden für die `IVsRunningDocumentTable4` Schnittstelle.  
  
- Wenn Ihre Erweiterung C++ verwendet wird, können Sie übergeben `null` für die Parameter, die Sie nicht möchten.  
  
- Sie können verhindern, dass unnötige Dokument laden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie die relevanten Eigenschaften einzuholen, bevor Sie andere Eigenschaften anfordern:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> Diese Methode gibt eine <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> -Objekt, das einen Wert für enthält <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , wenn das Dokument noch nicht initialisiert wurde.  
  
Sie können feststellen, wenn ein Dokument geladen wurde, indem Sie abonnieren das RDT-Ereignis, das ausgelöst wird, wenn ein Dokument vollständig initialisiert wurde. Es gibt zwei Möglichkeiten:  
  
- Wenn die Ereignissenke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- Andernfalls können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  

 Im folgende Beispiel ist ein hypothetisches Dokument-Access-Szenario: ein Visual Studio-Erweiterung möchte einige Informationen über geöffnete Dokumente angezeigt, z. B. die Bearbeitung zu sperren, Anzahl und etwas über die Dokumentdaten. Es listet die Dokumente in der RDT mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> für jedes Dokument, um die Sperre "Bearbeiten" die Daten für Count "und" Dokument abzurufen. Wenn das Dokument im Zustand "ausstehender-Initialization" ist, bewirkt, dass die Dokumentendaten anfordern unnötigerweise initialisiert werden.  
  
 Eine effizientere Methode für den Zugriff auf ein Dokument ist die Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> , rufen die Sperrenanzahl bearbeiten, und klicken Sie dann mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> zu bestimmen, ob das Dokument initialisiert wurde. Wenn die Flags nicht einbeziehen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, das Dokument wurde bereits initialisiert, und die Dokumentdaten mit anfordern <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> bewirkt nicht, dass unnötige Initialisierungen. Wenn die Flags umfassen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, die Erweiterung sollten die Daten anfordert, bis das Dokument initialisiert ist. Diese Initialisierung kann erkannt werden, der `OnAfterAttributeChange(Ex)` -Ereignishandler.  
  
## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testen Sie die Erweiterungen, um festzustellen, ob die Initialisierung zu erzwingen  
 Es gibt keinen sichtbaren Hinweis an, ob ein Dokument initialisiert wurde, damit es kann schwierig sein, herauszufinden, ob die Erweiterung Initialisierung erzwungen wird. Sie können einen Registrierungsschlüssel, die Überprüfung erleichtert, festlegen, da sie den Titel jedes Dokuments bewirkt, die für den Text nicht vollständig initialisiert ist *[Stub]* im Titel.  
  
 In **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**legen **StubTabTitleFormatString** zu  *{0} [Stub]*.