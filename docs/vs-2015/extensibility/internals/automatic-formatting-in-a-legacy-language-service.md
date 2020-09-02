---
title: Automatische Formatierung in einem Legacy Sprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157268"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatisches Formatieren in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bei der automatischen Formatierung fügt ein Sprachdienst automatisch einen Code Ausschnitt ein, wenn ein Benutzer damit beginnt, ein bekanntes Code Konstrukt einzugeben.  
  
## <a name="automatic-formatting-behavior"></a>Automatisches Formatierungs Verhalten  
 Wenn Sie z. b. eingeben `if` , fügt der Sprachdienst automatisch passende geschweifte Klammern ein, oder wenn Sie die EINGABETASTE drücken, erzwingt der Sprachdienst die Einfügemarke in der neuen Zeile auf die entsprechende Einzugs Ebene, je nachdem, ob die vorherige Zeile einen neuen Bereich öffnet.  
  
 Der für den Rest des sprach Dienstanbieter verwendete Befehls Filter kann auch für die automatische Formatierung verwendet werden. Sie können auch passende geschweifte Klammern hervorheben, indem Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
