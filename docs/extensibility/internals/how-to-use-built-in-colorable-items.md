---
title: 'Gewusst wie: Verwenden integrierter kolatyable Items | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905223"
---
# <a name="how-to-use-built-in-colorable-items"></a>Gewusst wie: Verwenden integrierter, Färb baren Elemente
Vor der Verwendung der integrierten färb baren Elemente müssen Sie zunächst ein Signal an die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) senden, dass Sie keine eigenen, benutzerdefinierten Elemente bereitstellen, die in diesem Fall <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Objekte sind. Hierzu legen Sie einen Registrierungs Eintrag für den Sprachdienst fest.

## <a name="to-use-built-in-colorable-items"></a>So verwenden Sie integrierte färb Bare Elemente

1. Erstellen Sie unter **HKEY_LOCAL_MACHINE \VisualStudio \\<X. Y> \Languages\Language Services \\<\> sprach Name**, wobei \<X.Y> eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und \<Language Name> der Name der Sprache ist. Erstellen Sie einen DWORD-Registrierungs Eintrags Wert namens **RequestStockColors**.

2. Legen Sie den Registrierungs Eintrags Wert **RequestStockColors** auf *1*fest.

    Nachdem Sie den Registrierungs Eintrag erstellt haben, kann die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode der Farbgebung die Member der- <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Enumeration verwenden, um das Array von Farb Attributen auszufüllen, die vom Editor verwendet werden sollen.

   > [!NOTE]
   > Legen Sie diesen Registrierungs Eintrag nicht fest, wenn Sie benutzerdefinierte Elemente bereitstellen. Weitere Informationen finden Sie unter [benutzerdefinierte Kolon-Elemente](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Weitere Informationen
- [Syntax Farbgebung in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntax Farben](../../extensibility/internals/implementing-syntax-coloring.md)
- [Benutzerdefinierte färb Bare Elemente](../../extensibility/internals/custom-colorable-items.md)
- [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service2.md)
