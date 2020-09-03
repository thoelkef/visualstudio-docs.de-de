---
title: Automatische Formatierung in einem Legacy Sprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709980"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatische Formatierung in einem Legacy Sprachdienst
Bei der automatischen Formatierung fügt ein Sprachdienst automatisch einen Code Ausschnitt ein, wenn ein Benutzer damit beginnt, ein bekanntes Code Konstrukt einzugeben.

## <a name="automatic-formatting-behavior"></a>Automatisches Formatierungs Verhalten
 Wenn Sie z. b. *eingeben,* fügt der Sprachdienst automatisch passende geschweifte Klammern ein, oder wenn Sie die EINGABETASTE drücken, erzwingt der Sprachdienst die Einfügemarke in der neuen Zeile auf die entsprechende Einzugs Ebene, je nachdem, ob die vorherige Zeile einen neuen Bereich öffnet.

 Der für den Rest des sprach Dienstanbieter verwendete Befehls Filter kann auch für die automatische Formatierung verwendet werden. Sie können auch passende geschweifte Klammern hervorheben, indem Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacy sprach Dienstanbieter](../../extensibility/internals/developing-a-legacy-language-service.md)
