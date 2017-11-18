---
title: Automatische Formatierung in einem Legacy-Sprachdienst | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09ab8a948011cdc53516ec21f0d213852166956
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatische Formatierung in einem Legacy-Sprachdienst
Mithilfe der automatischen Formatierung, fügt ein Sprachdienst automatisch einen Codeausschnitt ein, wenn ein Benutzer beginnt, geben Sie ein Codekonstrukt bekannte.  
  
## <a name="automatic-formatting-behavior"></a>Automatische Formatierungsverhalten  
 Wenn Sie z. B. eingeben `if`Sprachdiensts fügt automatisch die übereinstimmende geschweiften Klammern, oder wenn Sie die EINGABETASTE drücken, erzwingt des Sprachdiensts die Einfügemarke in der neuen Zeile auf die entsprechenden Einzugsebene, je nachdem, ob die vorangehenden Zeile wird ein neuer Bereich geöffnet.  
  
 Der für den Rest des Sprachdiensts verwendete Befehlsfilter kann auch für die automatische Formatierung verwendet werden. Sie können auch Klammern hervorheben, durch den Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)