---
title: Benutzerdefinierte kolorierbare Elemente | Microsoft-Dokumentation
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
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 272d16b9f5f8fb33b68c911c5e7bd27923f4c2db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796947"
---
# <a name="custom-colorable-items"></a>Benutzerdefinierte einfärbbare Elemente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können die Liste der Typen überschreiben, durch die Implementierung der benutzerdefinierten kolorierbaren Elemente als Teil Ihrer Sprachdienst für die farbliche Kennzeichnung, z. B. Schlüsselwörter und Kommentare.  
  
## <a name="user-settings-of-colorable-items"></a>Benutzereinstellungen der kolorierbaren Elemente  
 Anzeigen der **Schriftarten und Farben** Dialogfeld dazu **Optionen** auf die **Tools** Menü, und wählen Sie dann **Schriftarten und Farben** Klicken Sie unter **Umgebung**. Bei der Auswahl einer Anzeige, wie z. B. **Text-Editor** oder **Befehlsfenster**, wird die **Anzeigeelemente** Listenfeld zeigt alle für diese Anzeige kolorierbaren Elemente. Sie können anzeigen und Ändern der Schriftart, Größe, Vorder- und Hintergrundfarbe für jede kolorierbaren Elements. Ihre Auswahl werden in einem Cache in der Registrierung gespeichert und der Name des kolorierbaren Elements zugreifen.  
  
## <a name="presentation-of-colorable-items"></a>Darstellung der kolorierbaren Elemente  
 Da die IDE überschreibungen der kolorierbaren Elemente, die in verarbeitet der **Schriftarten und Farben** (Dialogfeld), müssen Sie nur jedes benutzerdefiniertes färbbares Element mit einem Namen angeben. Dieser Name ist scheinbar in der **Anzeigeelemente** Liste. Die kolorierbaren Elemente werden in alphabetischer Reihenfolge angezeigt. Um den Sprachdienst benutzerdefinierte kolorierbare Elemente zu gruppieren, können Sie z. B. den Namen durch den Sprachnamen Ihres beginnen **NewLanguage - Kommentar** und **NewLanguage - Schlüsselwort**.  
  
> [!CAUTION]
>  Der Name der Sprache aufzunehmen im Namen kolorierbaren Elements zum Vermeiden von Konflikten mit vorhandenen Namen der kolorierbaren Elements. Wenn Sie den Namen eines kolorierbaren Elemente während der Entwicklung ändern, müssen Sie den Cache zurücksetzen, der erstmalig erstellt wurde, die der kolorierbaren Elemente zugegriffen wurde. Sie können experimentelle Zurücksetzen des Caches mit dem CreateExpInstance-Tool, das mit Visual Studio SDK, in der Regel im Verzeichnis installiert wird  
>   
>  **C:\Programme\Microsoft Dateien (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Rufen Sie zum Zurücksetzen des Caches `CreateExpInstance /Reset`. Weitere Informationen zu CreateExpInstance, finden Sie unter [CreateExpInstance Utility](../../extensibility/internals/createexpinstance-utility.md).  
  
 Das erste Element in der Liste der kolorierbaren Elemente wird nie auf die verwiesen wird. Das erste Element entspricht einem kolorierbaren Elementindex 0 (null) und [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] der Standardfarben für Text und die Attribute für dieses Element immer bereitgestellt. Die einfachste Möglichkeit für den Umgang mit diesem nicht referenzierte Element ist ein Platzhalter färbbares Element in der Liste als erstes Element angeben.  
  
## <a name="implementing-custom-colorable-items"></a>Implementieren von benutzerdefinierten kolorierbaren Elemente  
  
1. Definieren Sie, was in Ihrer Sprache, z. B.-Schlüsselwort, Operator und Bezeichner farbig markiert werden muss.  
  
2. Erstellen Sie eine Enumeration, der diese kolorierbaren Elemente.  
  
3. Ordnen Sie die Tokentypen, die von einem Parser oder die Überprüfung mit den aufgelisteten Werten zurückgegeben.  
  
    Z. B. möglicherweise die Werte, die die Typen von Sicherheitstoken darstellt. die gleichen Werte in der benutzerdefinierten kolorierbaren Elemente-Enumeration.  
  
4. In der Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> -Methode in Ihrer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Objekt "," füllen die Liste der Attribute mit den Werten aus Ihrer benutzerdefinierten kolorierbaren Elemente-Enumeration, die für die Tokentypen, die von dem Parser oder der Überprüfung zurückgegeben.  
  
5. In der gleichen Klasse, die implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Schnittstelle und die zwei Methoden, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>-Schnittstelle.  
  
7. Wenn Sie 24-Bit-oder eine hohe Werte unterstützen möchten, implementieren Sie außerdem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle.  
  
8. In Ihrer Sprache-Dienstobjekt, erstellen Sie eine Liste mit Ihrem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Objekten, jeweils eines für die einzelnen kolorierbaren Elemente, die die Parser oder den Scanner identifizieren kann.  
  
    Sie können jedes Element in der Liste mit den entsprechenden Wert aus der Enumeration der benutzerdefinierten kolorierbaren Elemente zugreifen. Verwenden Sie die Enumerationswerte als Index, in der Liste. Das erste Element in der Liste wird nie zugegriffen werden, da es auf den Standardtext entspricht formatieren, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verarbeitet immer selbst. Sie können dies kompensieren, durch einen Platzhalter kolorierbare Element am Anfang der Liste einfügen.  
  
9. In der Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> -Methode, die Anzahl der Elemente in der Liste der benutzerdefinierten kolorierbaren Elemente zurück.  
  
10. In der Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> -Methode angeforderten kolorierbaren Elements aus der Liste zurückgeben.  
  
    Ein Beispiel zum Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstellen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Modell eines Legacysprachdiensts](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Syntaxfarben](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

