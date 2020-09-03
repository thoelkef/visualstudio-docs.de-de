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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196862"
---
# <a name="delayed-document-loading"></a>Verzögertes Laden von Dokumenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein Benutzer eine Visual Studio-Projekt Mappe erneut öffnet, werden die meisten zugeordneten Dokumente nicht sofort geladen. Der Dokument Fensterrahmen wird mit dem Status "ausstehende Initialisierung" erstellt, und ein Platzhalter Dokument (als Stub-Frame bezeichnet) wird in der ausgelaufenden dokumententabelle (RDT) platziert.  
  
 Die Erweiterung kann bewirken, dass Projektdokumente unnötig geladen werden, indem Sie Elemente in den Dokumenten Abfragen, bevor Sie geladen werden. Dadurch kann der Gesamt Speicherbedarf für Visual Studio erhöht werden.  
  
## <a name="document-loading"></a>Laden von Dokumenten  
 Der Stub-Frame und das Dokument werden vollständig initialisiert, wenn der Benutzer auf das Dokument zugreift, z. b. durch Auswählen der Registerkarte des Fensterrahmens. Das Dokument kann auch durch eine Erweiterung initialisiert werden, die die Daten des Dokuments anfordert, indem Sie entweder direkt auf den RDT zugreifen, um die Dokument Daten abzurufen, oder indirekt auf den RDT zugreifen, indem Sie einen der folgenden Aufrufe durchführen:  
  
- Die Fenster Frame Show-Methode: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- Die GetProperty-Methode für den Fensterrahmen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> einer der folgenden Eigenschaften:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Wenn die Erweiterung verwalteten Code verwendet, sollten Sie nicht aufzurufen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> es sei denn, Sie sind sicher, dass sich das Dokument nicht im Status der ausstehenden Initialisierung befindet oder ob das Dokument vollständig initialisiert werden soll. Dies liegt daran, dass diese Methode immer das doc-Datenobjekt zurückgibt und es bei Bedarf erstellt. Stattdessen sollten Sie eine der-Methoden in der IVsRunningDocumentTable4-Schnittstelle abrufen.  
  
  Wenn die Erweiterung C++ verwendet, können Sie `null` für die Parameter übergeben, die Sie nicht möchten.  
  
  Sie können unnötige Laden von Dokumenten vermeiden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie nach den relevanten Eigenschaften Fragen: bevor Sie weitere Eigenschaften anfordern.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Verwenden von <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Diese Methode gibt ein- <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Objekt zurück, das einen Wert für enthält, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Wenn das Dokument noch nicht initialisiert wurde.  
  
  Sie können herausfinden, wann ein Dokument geladen wurde, indem Sie das RDT-Ereignis abonnieren, das ausgelöst wird, wenn ein Dokument vollständig initialisiert wurde. Es gibt zwei Möglichkeiten:  
  
- Wenn die Ereignis Senke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> .  
  
- Andernfalls können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Im folgenden finden Sie ein hypothetisches Dokument Zugriffs Szenario. Eine Visual Studio-Erweiterung möchte einige Informationen zu geöffneten Dokumenten anzeigen, beispielsweise die Anzahl der Bearbeitungs Sperren und etwas über die Dokument Daten. Die Dokumente werden im RDT mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> von aufgelistet. Anschließend wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> für jedes Dokument aufgerufen, um die Anzahl der Bearbeitungs Sperren und die Dokument Daten abzurufen. Wenn sich das Dokument im Zustand "ausstehende Initialisierung" befindet, bewirkt das Anfordern der Dokument Daten, dass es unnötig initialisiert wird.  
  
  Eine effizientere Methode hierfür ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> die Verwendung von zum Ermitteln der Anzahl der Bearbeitungs Sperren und die anschließende Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> von, um zu bestimmen, ob das Dokument initialisiert wurde. Wenn die Flags nicht enthalten <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , wurde das Dokument bereits initialisiert, und das Anfordern der Dokument Daten mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> verursacht keine unnötige Initialisierung. Wenn die Flags einschließen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , sollte die Erweiterung die Dokument Daten erst anfordern, wenn das Dokument initialisiert wird. Dies kann im Ereignishandler onafterattributechange (ex) erkannt werden.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testen von Erweiterungen, um festzustellen, ob Sie die Initialisierung erzwingen  
 Es gibt keinen sichtbaren Hinweis, der angibt, ob ein Dokument initialisiert wurde. Daher kann es schwierig sein, herauszufinden, ob die Erweiterung die Initialisierung erzwingt. Sie können einen Registrierungsschlüssel festlegen, der die Überprüfung vereinfacht, da der Titel jedes Dokuments, das nicht vollständig initialisiert ist, den Text `[Stub]` im Titel enthält.  
  
 Legen Sie in **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** **stubtabtitleformatstring** auf ** {0} [Stub]** fest.
