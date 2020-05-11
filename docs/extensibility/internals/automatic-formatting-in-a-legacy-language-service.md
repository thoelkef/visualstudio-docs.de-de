---
title: Automatische formatierung in einem Legacy-Sprachdienst | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709980"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatische Formatierung in einem älteren Sprachdienst
Bei der automatischen Formatierung fügt ein Sprachdienst automatisch einen Codeausschnitt ein, wenn ein Benutzer mit der Eingabe eines bekannten Codekonstrukts beginnt.

## <a name="automatic-formatting-behavior"></a>Automatisches Formatierungsverhalten
 Wenn Sie z. B. *if*eingeben, fügt der Sprachdienst automatisch übereinstimmende geschweifte Klammern ein, oder wenn Sie die ENTER-Taste drücken, erzwingt der Sprachdienst die Einfügemarke in der neuen Zeile auf die entsprechende Einzugsebene, je nachdem, ob die vorherige Zeile einen neuen Bereich öffnet.

 Der Befehlsfilter, der für den Rest des Sprachdienstes verwendet wird, kann auch für die automatische Formatierung verwendet werden. Sie können auch übereinstimmende <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>geschweifte Klammern hervorheben, indem Sie aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines älteren Sprachdienstes](../../extensibility/internals/developing-a-legacy-language-service.md)
