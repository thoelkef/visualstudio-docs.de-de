---
title: Automatische Formatierung in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b69419e917a5ab5293af15b21822ca6473a9e292
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344932"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatische Formatierung in einem legacy-Sprachdienst
Mithilfe der automatischen Formatierung Fügt ein Sprachdienst automatisch einen Codeausschnitt ein, wenn ein Benutzer damit beginnt, geben Sie ein bekanntes-Codekonstrukt.

## <a name="automatic-formatting-behavior"></a>Automatische Formatierung Verhalten
 Wenn Sie z. B. Typ *Wenn*, der Sprachdienst fügt automatisch die übereinstimmende geschweiften Klammern oder wenn Sie die EINGABETASTE drücken, erzwingt des Sprachdiensts die Einfügemarke in der neuen Zeile auf die entsprechenden Einzugsebene, je nach Gibt an, ob die vorangehende Zeile ein neuer Bereich geöffnet wird.

 Der Befehlsfilter verwendet, für den Rest des Sprachdiensts kann auch für die automatische Formatierung verwendet werden. Sie können auch Klammern hervorheben, durch den Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.

## <a name="see-also"></a>Siehe auch
- [Entwickeln eines Datendiensts legacysprache](../../extensibility/internals/developing-a-legacy-language-service.md)