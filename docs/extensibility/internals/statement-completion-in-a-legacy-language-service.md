---
title: Anweisungsabschluss in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704942"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Anweisungsvervollständigung in einem Legacysprachdienst
Die Anweisungsvervollständigung ist der Prozess, mit dem der Sprachdienst Benutzern hilft, ein Sprachschlüsselwort oder -element zu beenden, das sie im Kerneditor eingegeben haben. In diesem Thema wird erläutert, wie die Anweisungsvervollständigung funktioniert und wie sie in Ihrem Sprachdienst implementiert werden.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren der Anweisungsvervollständigung finden Sie unter [Walkthrough: Displaying Statement Completion](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="implementing-statement-completion"></a>Implementierungserklärungsabschluss
 Im Kerneditor aktiviert die Anweisungsvervollständigung eine spezielle Benutzeroberfläche, die Ihnen interaktiv hilft, Code einfacher und schneller zu schreiben. Die Anweisungsvervollständigung hilft, indem relevante Objekte oder Klassen angezeigt werden, wenn sie benötigt werden, wodurch Sie bestimmte Elemente oder sie in einem Hilfereferenzthema nachschlagen müssen.

 Um die Anweisungsvervollständigung zu implementieren, muss Ihre Sprache über einen Anweisungsvervollständigungstrigger verfügen, der analysiert werden kann. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Verwendet z. B. einen Punktoperator [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] (.), während ein Pfeiloperator (->) verwendet wird. Ein Sprachdienst kann mehr als einen Trigger verwenden, um den Abschluss der Anweisung zu initiieren. Diese Trigger werden im Befehlsfilter programmiert.

## <a name="command-filters-and-triggers"></a>Befehlsfilter und Trigger
 Befehlsfilter fangen Vorkommen Ihres Triggers oder Triggers ab. Um den Befehlsfilter zur Ansicht <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> hinzuzufügen, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Schnittstelle, und fügen Sie sie an die Ansicht an, indem Sie die Methode aufrufen. Sie können denselben Befehlsfilter (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) für alle Aspekte des Sprachdienstes verwenden, z. B. Anweisungsvervollständigung, Fehlermarkierungen und Methodentipps. Weitere Informationen finden Sie unter [Abfangen von Legacy Language Service Commands](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Wenn der Trigger im Editor eingegeben wird , insbesondere der Textpuffer – ruft Ihr Sprachdienst dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode auf. Dadurch wird die Benutzeroberfläche vom Editor angezeigt, sodass der Benutzer aus den Abschlusskandidaten für die Anweisung auswählen kann. Diese Methode erfordert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> die <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> Implementierung und die Flags als Parameter. Die Liste der Vervollständigungselemente wird in einem Bildlauflistenfeld angezeigt. Wenn der Benutzer die Eingabe fortsetzt, wird die Auswahl im Listenfeld aktualisiert, um die Übereinstimmung mit den zuletzt eingegebenen Zeichen widerzuspiegeln. Der Kerneditor implementiert die Benutzeroberfläche für den Abschluss <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> der Anweisung, aber der Sprachdienst muss die Schnittstelle implementieren, um eine Reihe von Kandidatenabschlusselementen für die Anweisung zu definieren.

## <a name="see-also"></a>Weitere Informationen
- [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
