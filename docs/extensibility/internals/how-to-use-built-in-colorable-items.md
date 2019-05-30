---
title: 'Vorgehensweise: Verwenden Sie die integrierten kolorierbaren Elemente | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae1c327c14ed2b349ee02566c5cdfd38b9a07859
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311969"
---
# <a name="how-to-use-built-in-colorable-items"></a>Vorgehensweise: Verwenden Sie die integrierten kolorierbaren Elemente
Bevor Sie die integrierten kolorierbaren Elemente verwenden, Sie müssen zuerst signalisieren die integrierte Entwicklungsumgebung (IDE), dass Sie nicht Ihre eigenen benutzerdefinierten kolorierbaren Elemente bereitstellen, die in diesem Fall würde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Objekte. Dazu müssen Sie einen Registrierungseintrag für den Sprachdienst festlegen.

## <a name="to-use-built-in-colorable-items"></a>Verwenden von integrierten einfärbbaren Elementen

1. Klicken Sie unter **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language Services\\< Sprachenname\>** , wobei \<X.Y > ist eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und \<Sprachenname > ist der Name der Sprache, erstellen Sie einen DWORD-Registrierungswert Eintrag namens **RequestStockColors**.

2. Legen Sie die **RequestStockColors** registrierungseintragswert zu *1*.

    Nach der Erstellung des Registrierungseintrags, Ihre Farbauswahl des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode können die Mitglieder der <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Enumeration das Array von Farbattributen, die für die Verwendung durch den Editor eingeben.

   > [!NOTE]
   > Legen Sie dieses Registrierungseintrags nicht, wenn Sie eine benutzerdefinierte kolorierbare Elemente bereitstellen. Weitere Informationen finden Sie unter [benutzerdefinierten kolorierbaren Elemente](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Siehe auch
- [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Syntaxfarben in einem legacysprachdiensten](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntaxfarben](../../extensibility/internals/implementing-syntax-coloring.md)
- [Benutzerdefinierte kolorierbare Elemente](../../extensibility/internals/custom-colorable-items.md)
- [Registrieren von Diensten legacysprache](../../extensibility/internals/registering-a-legacy-language-service2.md)