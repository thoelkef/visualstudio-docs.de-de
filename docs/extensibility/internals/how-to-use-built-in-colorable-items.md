---
title: 'Gewusst wie: Verwenden von integrierten farbbaren Elementen | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707789"
---
# <a name="how-to-use-built-in-colorable-items"></a>Gewusst wie: Verwenden Sie integrierte farbbare Elemente
Bevor Sie die integrierten befärbbaren Elemente verwenden, müssen Sie der integrierten Entwicklungsumgebung (IDE) zunächst signalisieren, dass <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Sie keine eigenen benutzerdefinierten befärbbaren Elemente bereitstellen, die in diesem Fall Objekte wären. Dazu legen Sie einen Registrierungseintrag für den Sprachdienst fest.

## <a name="to-use-built-in-colorable-items"></a>So verwenden Sie integrierte farbbare Elemente

1. Erstellen Sie unter **HKEY_LOCAL_MACHINE-VisualStudio-<\\ X.Y->-Sprachen-Sprachdienste\\<Sprachnamen\>**, wobei \<X.Y> eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist und \<Language Name> der Name Ihrer Sprache ist, einen DWORD-Registrierungseintragswert namens **RequestStockColors**.

2. Legen Sie den **Registrierungseintragswert RequestStockColors** auf *1*fest.

    Nachdem Sie den Registrierungseintrag erstellt haben, kann die Methode des Colorizers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> die Member der <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Enumeration verwenden, um das Array von Farbattributen für die Verwendung durch den Editor auszufüllen.

   > [!NOTE]
   > Legen Sie diesen Registrierungseintrag nicht fest, wenn Sie benutzerdefinierte befärbbare Elemente bereitstellen. Weitere Informationen finden Sie unter [Benutzerdefinierte befärbbare Elemente](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Weitere Informationen
- [Syntaxfärbung in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Syntaxfarben in einem älteren Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren der Syntaxfärbung](../../extensibility/internals/implementing-syntax-coloring.md)
- [Benutzerdefinierte farbbare Artikel](../../extensibility/internals/custom-colorable-items.md)
- [Registrieren eines älteren Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service2.md)
