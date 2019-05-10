---
title: Verzögertes Laden von Dokumenten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116926"
---
# <a name="delayed-document-loading"></a>Verzögertes Laden von Dokumenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein Benutzer mit Visual Studio-Projektmappe erneut öffnet, werden die meisten der zugehörigen Dokumente nicht sofort geladen werden. Die dokumentfensterrahmen wird in einem Zustand ausstehende Initialisierung erstellt, und ein Platzhalterdokument (einen Stub-Frame bezeichnet) befindet sich in der ausführen-Dokumenten-Tabelle (RDT).  
  
 Die Erweiterung möglicherweise Projektdokumente unnötigerweise geladen werden, durch Abfragen von Elementen in den Dokumenten, bevor sie geladen werden. Dies kann Gesamtspeicherbedarf für Visual Studio erhöhen.  
  
## <a name="document-loading"></a>Laden von Dokumenten  
 Dokument mit den Stub-Frames und sind vollständig initialisiert, wenn der Benutzer das Dokument, z. B. greift auf durch Auswählen der Registerkarte des Fensterrahmens. Das Dokument kann auch von einer Erweiterung initialisiert werden, die die Daten eines Dokuments, entweder durch den Zugriff auf den RDT direkt, um die Daten zu erhalten oder den Zugriff auf den RDT indirekt selbst eines der folgenden Aufrufe anfordert:  
  
- Anzeigen des fensterframes-Methode: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
- Der Fensterrahmen GetProperty-Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> auf einem der folgenden Eigenschaften:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Wenn Ihre Erweiterung verwalteten Code verwendet wird, sollten Sie nicht aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> es sei denn, Sie sicher, dass das Dokument ist nicht im Zustand "ausstehender-Initialization" oder das Dokument vollständig initialisiert werden soll... Dies ist, da diese Methode immer die Doc gibt-Datenobjekt, wodurch bei Bedarf erstellt. Stattdessen müssen Sie eine der Methoden für die IVsRunningDocumentTable4-Schnittstelle aufrufen.  
  
  Wenn Ihre Erweiterung C++ verwendet wird, können Sie übergeben `null` für die Parameter, die Sie nicht möchten.  
  
  Sie können unnötige Dokument laden vermeiden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie die relevanten Eigenschaften anfordern: Bevor Sie andere Eigenschaften anfordern.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Diese Methode gibt eine <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> -Objekt, das einen Wert für enthält <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , wenn das Dokument noch nicht initialisiert wurde.  
  
  Sie können feststellen, wenn ein Dokument geladen wurde, indem Sie abonnieren das RDT-Ereignis, das ausgelöst wird, wenn ein Dokument vollständig initialisiert wurde. Es gibt zwei Möglichkeiten:  
  
- Wenn die Ereignissenke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- Andernfalls können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
  Im folgenden wird ein Szenario mit hypothetischen Dokument Zugriff. Ein Visual Studio Extension einige Informationen über geöffnete Dokumente angezeigt werden soll, z. B. die Bearbeitung gesperrt werden Anzahl und etwas über die Dokumentdaten. Es listet die Dokumente in der RDT mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> für jedes Dokument, um die Sperre "Bearbeiten" die Daten für Count "und" Dokument abzurufen. Wenn das Dokument im Zustand "ausstehender-Initialization" ist, bewirkt, dass die Dokumentendaten anfordern unnötigerweise initialisiert werden.  
  
  Eine effizientere Möglichkeit dafür ist Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> , rufen die Sperrenanzahl bearbeiten, und klicken Sie dann mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> zu bestimmen, ob das Dokument initialisiert wurde. Wenn die Flags nicht einbeziehen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, das Dokument wurde bereits initialisiert, und die Dokumentdaten mit anfordern <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> bewirkt nicht, dass unnötige Initialisierungen. Wenn die Flags umfassen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, die Erweiterung sollten die Daten anfordert, bis das Dokument initialisiert ist. Dies kann im Ereignishandler OnAfterAttributeChange(Ex) erkannt werden.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testen die Erweiterungen, um festzustellen, ob die Initialisierung zu erzwingen  
 Es gibt keinen sichtbaren Hinweis an, ob ein Dokument initialisiert wurde, damit es kann schwierig sein, herauszufinden, ob die Erweiterung Initialisierung erzwungen wird. Sie können einen Registrierungsschlüssel, die Überprüfung erleichtert, festlegen, da sie den Titel jedes Dokuments bewirkt, die für den Text nicht vollständig initialisiert ist `[Stub]` im Titel.  
  
 In **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]** legen **StubTabTitleFormatString** zu  **{0} [Stub]**.
