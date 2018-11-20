---
title: Automatische Formatierung in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1e9be96038334edeb9163c15d16a98999bd0c2e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795491"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatisches Formatieren in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mithilfe der automatischen Formatierung Fügt ein Sprachdienst automatisch einen Codeausschnitt ein, wenn ein Benutzer damit beginnt, geben Sie ein bekanntes-Codekonstrukt.  
  
## <a name="automatic-formatting-behavior"></a>Automatische Formatierung Verhalten  
 Z. B. bei der Eingabe `if`, der Sprachdienst fügt automatisch die übereinstimmende geschweiften Klammern oder wenn Sie die EINGABETASTE drücken, erzwingt des Sprachdiensts die Einfügemarke in der neuen Zeile auf die entsprechenden Einzugsebene, je nachdem, ob der vorherigen Zeile wird ein neuer Bereich geöffnet.  
  
 Der Befehlsfilter verwendet, für den Rest des Sprachdiensts kann auch für die automatische Formatierung verwendet werden. Sie können auch Klammern hervorheben, durch den Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)

