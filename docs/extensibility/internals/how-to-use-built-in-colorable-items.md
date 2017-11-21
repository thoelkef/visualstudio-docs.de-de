---
title: "Vorgehensweise: Verwenden von integrierten Färbbare Elemente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 519b842f99ff3e4460626b82aafd24a02f9e720d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-built-in-colorable-items"></a>Vorgehensweise: Verwenden von integrierten Färbbare Elemente
Vor der Verwendung der integrierten färbbare Elemente Sie müssen zuerst darauf hinweisen, der integrierten Entwicklungsumgebung (IDE), dass Sie keine eigene benutzerdefinierte färbbare Elemente bereitstellen, der in diesem Fall wäre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Objekte. Dazu müssen Sie einen Registrierungseintrag für den Sprachdienst festlegen.  
  
### <a name="to-use-built-in-colorable-items"></a>Verwenden von integrierten färbbare Elemente  
  
1.  Unter HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language Services\\*Sprachenname*, wobei *X.Y* ist eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und *Sprachenname* ist der Name Ihrer Programmiersprache, erstellen Sie einen DWORD-Registrierungswert Eintrag namens `RequestStockColors`.  
  
2.  Legen Sie die `RequestStockColors` Eintrag Registrierungswert auf 1.  
  
     Nach der Erstellung der Registrierungseintrag, der Colorizer des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode können die Mitglieder der <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> füllen Sie das Array von Attributen der Farbe für die Verwendung durch die Editor-Enumeration.  
  
    > [!NOTE]
    >  Dieser Registrierungseintrag kann nicht festgelegt werden, wenn Sie benutzerdefinierte färbbare Elemente bereitstellen. Weitere Informationen finden Sie unter [benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Syntaxfarben in einen Legacy-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren die Farben für Syntax](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md)   
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)