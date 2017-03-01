---
title: Verwendung von RDT_ReadLock | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock Verwendung

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>ist ein Flag, das stellt die Logik für das Sperren eines Dokuments in der ausgeführten Dokument Tabelle (RDT), dies ist die Liste aller Dokumente, die in der Visual Studio IDE geöffnet sind.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Dieses Flag wird bestimmt, wenn Dokumente geöffnet sind, und gibt an, ob ein Dokument in der Benutzeroberfläche sichtbar oder unsichtbar im Arbeitsspeicher gehalten wird.

Im Allgemeinen verwenden Sie <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>, wenn eine der folgenden Aussagen zutrifft:</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- Wenn Sie ein Dokument im Hintergrund öffnen möchten und schreibgeschützt, aber es noch nicht festgelegt, welche <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>it. besitzen sollten</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- Wenn Sie möchten die Benutzer aufgefordert, ein Dokument zu speichern, die im Hintergrund geöffnet wurde, bevor der Benutzer es in der Benutzeroberfläche angezeigt und dann versucht, es zu schließen.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Verwalten von sichtbar bzw. unsichtbar Dokumente

Wenn ein Benutzer ein Dokument in der Benutzeroberfläche öffnet ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Besitzer des Dokuments muss eingerichtet werden und ein <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>Flag muss festgelegt werden.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Wenn kein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Besitzer hergestellt werden kann, und klicken Sie dann das Dokument wird nicht gespeichert werden, klickt der Benutzer **alle** oder schließt die IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Dies bedeutet, wenn ein Dokument geöffnet nicht sichtbar ist, in denen es im Arbeitsspeicher nicht geändert wurde und der Benutzer aufgefordert, das Dokument zu speichern, beim Herunterfahren oder gespeichert werden, wenn **alle** ausgewählt wird, wird eine `RDT_ReadLock` kann nicht verwendet werden. Stattdessen müssen Sie verwenden ein `RDT_EditLock` und registrieren Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>beim ein <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>Flag.</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock und Dokument ändern

Das vorherige Flag erwähnt gibt an, dass das unsichtbare Öffnen des Dokuments erzielt werden die `RDT_EditLock` beim Öffnen des Dokuments durch den Benutzer in ein sichtbares **DocumentWindow**. In diesem Fall wird dem Benutzer angezeigt, mit einem **speichern** aufgefordert, wenn der sichtbaren **DocumentWindow** geschlossen wird. <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>Implementierungen, mit denen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>Dienst anfänglich arbeiten, wenn nur ein `RDT_ReadLock` stammt (d. h., wenn das Dokument im Hintergrund geöffnet wird, um Informationen zu analysieren).</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> Später, wenn das Dokument geändert werden muss, klicken Sie dann die Sperre auf aktualisiert wird eine schwache **RDT_EditLock**. Wenn der Benutzer das Dokument in ein sichtbares dann öffnet **DocumentWindow**, `CodeModel`des schwachen `RDT_EditLock` veröffentlicht wird.

Wenn der Benutzer dann schließt die **DocumentWindow** und wählt die **keine** Aufforderung zum Speichern der geöffneten Dokuments, die `CodeModel` Implementierung verwirft alle Informationen im Dokument und öffnet das Dokument vom Datenträger im Hintergrund das nächste Mal Informationen erforderlich für das Dokument ist. Die Besonderheit dieses Verhalten ist eine Instanz, in dem der Benutzer öffnet, die **DocumentWindow** des unsichtbaren geöffneten Dokuments ändert, wird geschlossen und wählt dann **Nr.** bei der Aufforderung zum Speichern des Dokuments. In diesem Fall, wenn das Dokument besitzt einen `RDT_ReadLock`, das Dokument wird nicht geschlossen werden, und das geänderte Dokument bleibt geöffnet, im Hintergrund im Speicher, obwohl der Benutzer hat nicht das Dokument zu speichern.

Wenn das unsichtbare Öffnen des Dokuments eine schwache verwendet `RDT_EditLock`, dann gibt er eine Sperre, wenn der Benutzer das Dokument sichtbar öffnet und keine anderen Sperren aufrechterhalten werden. Der Benutzer schließt die **DocumentWindow** und **keine** Wenn aufgefordert, das Dokument zu speichern, klicken Sie dann das Dokument muss geschlossen werden, aus dem Speicher. Das bedeutet, die unsichtbar Client RDT Ereignisse auftreten überwachen muss. Das nächste Mal das Dokument erforderlich ist, muss das Dokument erneut geöffnet werden.
