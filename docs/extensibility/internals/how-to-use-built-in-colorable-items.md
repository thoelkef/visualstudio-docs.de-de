---
title: 'Vorgehensweise: Verwenden von integrierten Färbbare Elemente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6cf51516677aeca71dba269bcdd132e0830b6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129682"
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