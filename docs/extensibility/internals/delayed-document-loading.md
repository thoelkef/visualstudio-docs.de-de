---
title: Verzögertes Laden von Dokumenten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708812"
---
# <a name="delayed-document-loading"></a>Verzögertes Laden von Dokumenten

Wenn ein Benutzer eine Visual Studio-Lösung erneut öffnet, werden die meisten zugeordneten Dokumente nicht sofort geladen. Der Dokumentfensterrahmen wird in einem Zustand der Auslaufinitialisierung erstellt, und ein Platzhalterdokument (als Stubframe bezeichnet) wird in der Tabelle "Laufendes Dokument" (RDT) platziert.

Ihre Erweiterung kann dazu führen, dass Projektdokumente unnötig geladen werden, indem Elemente in den Dokumenten abgefragt werden, bevor sie geladen werden, was den gesamten Speicherbedarf für Visual Studio erhöhen kann.

## <a name="document-loading"></a>Laden von Dokumenten

Der Stubrahmen und das Dokument werden vollständig initialisiert, wenn der Benutzer auf das Dokument zugreift, z. B. indem er die Registerkarte des Fensterrahmens auswählt. Das Dokument kann auch durch eine Erweiterung initialisiert werden, die die Daten des Dokuments anfordert, entweder durch direkten Zugriff auf die RDT, um die Dokumentdaten zu erfassen, oder durch indirektes Zugreifen auf die RDT durch einen der folgenden Aufrufe:

- Die Fensterrahmenmethode. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>

- Die Fensterrahmenmethode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> für eine der folgenden Eigenschaften:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Wenn Ihre Erweiterung verwalteten Code <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> verwendet, sollten Sie nur aufrufen, wenn Sie sicher sind, dass sich das Dokument nicht im Zustand der ausstehenden Initialisierung befindet, oder Sie möchten, dass das Dokument vollständig initialisiert wird. Der Grund dafür ist, dass die Methode immer das Doc-Datenobjekt zurückgibt und es bei Bedarf erstellt. Stattdessen sollten Sie eine der Methoden `IVsRunningDocumentTable4` auf der Schnittstelle aufrufen.

- Wenn Ihre Erweiterung C++ verwendet, können Sie die Parameter übergeben, die Sie nicht möchten. `null`

- Sie können unnötiges Laden von Dokumenten vermeiden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie nach den entsprechenden Eigenschaften fragen, bevor Sie nach anderen Eigenschaften fragen:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>mit [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Diese Methode <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> gibt ein Objekt zurück, das einen Wert für [_VSRDTFLAGS4 enthält. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) wenn das Dokument noch nicht initialisiert wurde.

Sie können herausfinden, wann ein Dokument geladen wurde, indem Sie das RDT-Ereignis abonnieren, das ausgelöst wird, wenn ein Dokument vollständig initialisiert wird. Es gibt zwei Möglichkeiten:

- Wenn die Ereignissenke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>wird, können Sie abonnieren,

- Andernfalls können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.

Das folgende Beispiel ist ein hypothetisches Dokumentzugriffsszenario: Eine Visual Studio-Erweiterung möchte einige Informationen zu geöffneten Dokumenten anzeigen, z. B. die Anzahl der Bearbeitungssperren und etwas über die Dokumentdaten. Es zählt die Dokumente in der <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>RDT <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> mit , ruft dann für jedes Dokument auf, um die Bearbeitungssperranzahl und Dokumentdaten abzurufen. Wenn sich das Dokument im Zustand der ausstehenden Initialisierung befindet, führt das Anfordern der Dokumentdaten dazu, dass es unnötig initialisiert wird.

Eine effizientere Methode zum Zugriff auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> ein Dokument besteht darin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> die Anzahl der Bearbeitungssperren abzulesen und dann zu bestimmen, ob das Dokument initialisiert wurde. Wenn die Flags keine [_VSRDTFLAGS4 enthalten. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)wurde das Dokument bereits initialisiert, und <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> das Anfordern der Dokumentdaten mit verursacht keine unnötige Initialisierung. Wenn die Flags [_VSRDTFLAGS4 enthalten. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)sollte die Erweiterung vermeiden, die Dokumentdaten anzufordern, bis das Dokument initialisiert wurde. Diese Initialisierung kann im `OnAfterAttributeChange(Ex)` Ereignishandler erkannt werden.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testen Sie Erweiterungen, um zu sehen, ob sie die Initialisierung erzwingen

Es gibt keinen sichtbaren Hinweis, der angibt, ob ein Dokument initialisiert wurde, daher kann es schwierig sein, herauszufinden, ob Ihre Erweiterung die Initialisierung erzwingt. Sie können einen Registrierungsschlüssel festlegen, der die Überprüfung vereinfacht, da der Titel jedes Dokuments, das nicht vollständig initialisiert ist, den Text *[Stub]* im Titel enthält.

Legen Sie StubTabTitleFormatString in **HKEY_CURRENT_USER -software,Microsoft-VisualStudio-14.0-BackgroundSolutionLoad**fest, **stubTabTitleFormatString** auf * {0} [Stub]*.
