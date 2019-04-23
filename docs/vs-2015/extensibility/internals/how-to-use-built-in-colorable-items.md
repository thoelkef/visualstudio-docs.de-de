---
title: 'Vorgehensweise: Verwenden Sie die integrierten kolorierbaren Elemente | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 21a2b520111c07b6c964eae19f5a6064e926db70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039982"
---
# <a name="how-to-use-built-in-colorable-items"></a>Vorgehensweise: Verwenden von integrierten einfärbbaren Elementen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bevor Sie die integrierten kolorierbaren Elemente verwenden, Sie müssen zuerst signalisieren die integrierte Entwicklungsumgebung (IDE), dass Sie nicht Ihre eigenen benutzerdefinierten kolorierbaren Elemente bereitstellen, die in diesem Fall würde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Objekte. Dazu müssen Sie einen Registrierungseintrag für den Sprachdienst festlegen.  
  
### <a name="to-use-built-in-colorable-items"></a>Verwenden von integrierten einfärbbaren Elementen  
  
1. Unter HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language Services\\*Sprachenname*, wobei *X.Y* ist eine Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und *Sprachenname* ist der Name der Sprache, erstellen Sie einen DWORD-Registrierungswert Eintrag namens `RequestStockColors`.  
  
2. Legen Sie die `RequestStockColors` registrierungseintragswert auf 1.  
  
     Nach der Erstellung des Registrierungseintrags, Ihre Farbauswahl des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode können die Mitglieder der <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Enumeration das Array von Farbattributen, die für die Verwendung durch den Editor eingeben.  
  
    > [!NOTE]
    >  Legen Sie dieses Registrierungseintrags nicht, wenn Sie eine benutzerdefinierte kolorierbare Elemente bereitstellen. Weitere Informationen finden Sie unter [benutzerdefinierten kolorierbaren Elemente](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Syntaxfarben](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Benutzerdefinierte kolorierbare Elemente](../../extensibility/internals/custom-colorable-items.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service2.md)
