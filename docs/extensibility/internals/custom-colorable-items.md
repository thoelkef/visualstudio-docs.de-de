---
title: Benutzerdefinierte Färbbare Elemente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b23ff39abcb9a1354ea28becab3b7df867378ddf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133371"
---
# <a name="custom-colorable-items"></a>Benutzerdefinierte Färbbare Elemente
Sie können die Liste der Typen überschreiben implementieren benutzerdefinierte färbbare Elemente als Teil der Sprachdienst für die farbliche Kennzeichnung, z. B. Schlüsselwörter und Kommentare.  
  
## <a name="user-settings-of-colorable-items"></a>Benutzereinstellungen Färbbare Elemente  
 Anzeigen der **Schriftarten und Farben** Dialogfeld dazu **Optionen** auf die **Tools** Menü, und wählen Sie dann **Schriftarten und Farben** Klicken Sie unter **Umgebung**. Bei Auswahl eine Anzeige, z. B. **Text-Editor** oder **Befehlsfenster**, **Einblenden von Elementen** Listenfeld zeigt alle färbbare Elemente zur Anzeige von. Sie können anzeigen und ändern Schriftart, Größe, Vordergrundfarbe und die Hintergrundfarbe für jede färbbare Element. Ihre Auswahl in einem Cache in der Registrierung gespeichert und mit dem Namen färbbare Element zugegriffen.  
  
## <a name="presentation-of-colorable-items"></a>Darstellung der Färbbare Elemente  
 Da die IDE Benutzer Außerkraftsetzungen der färbbare Elemente in verarbeitet der **Schriftarten und Farben** (Dialogfeld), müssen Sie nur jede benutzerdefiniertes färbbare Element mit einem Namen angeben. Dieser Name wird in der **Elemente anzeigen** Liste. Die färbbare Elemente werden in alphabetischer Reihenfolge angezeigt. Um Ihre Sprachdienst benutzerdefinierte färbbare Elemente zu gruppieren, Sie den Namen durch Ihre Sprachenname, z. B. beginnen **NewLanguage - Kommentar** und **NewLanguage - Schlüsselwort**.  
  
> [!CAUTION]
>  Der Name der Sprache aufzunehmen im Namen färbbare Element zum Vermeiden von Konflikten mit vorhandenen Namen von färbbare Element. Wenn Sie den Namen einer Ihrer färbbare Elemente während der Entwicklung ändern, müssen Sie den Cache zurücksetzen, der Ihre färbbare Elemente auf die zugegriffen wurde erstmalig erstellt wurde. Sie können die experimentellen Cache mit dem Tool CreateExpInstance zurückgesetzt, d. h. mit der Visual Studio-SDK, in der Regel im Verzeichnis installiert ist  
>   
>  **C:\Programme\Microsoft Dateien (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Rufen Sie zum Zurücksetzen des Caches `CreateExpInstance /Reset`. Weitere Informationen zu CreateExpInstance, finden Sie unter [CreateExpInstance-Hilfsprogramm](../../extensibility/internals/createexpinstance-utility.md).  
  
 Das erste Element in der Liste der färbbare Elemente wird nie auf die verwiesen wird. Das erste Element entspricht einem färbbare Elementindex 0 (null) und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt immer die Standardfarben für Text und die Attribute für dieses Element. Die einfachste Möglichkeit für den Umgang mit diesem Unreferenzierte Element ist ein Platzhalter färbbare Element in der Liste als erstes Element angeben.  
  
## <a name="implementing-custom-colorable-items"></a>Implementieren benutzerdefinierte Färbbare Elemente  
  
1.  Definieren Sie, was in Ihrer Sprache, z. B.-Schlüsselwort, Operator und Bezeichner farbig hervorgehoben werden muss.  
  
2.  Erstellen Sie eine Enumeration färbbare Elemente.  
  
3.  Ordnen Sie die Tokentypen von Parser oder Scanner mit aufgezählter Werte zurückgegeben.  
  
     Die Werte, die den Tokentypen darstellt könnte z. B. den gleichen Werten in der Enumeration benutzerdefinierte färbbare Elemente sein.  
  
4.  In der Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode in Ihrer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Objekt "," Füllen Sie die Liste "Attribute" mit den Werten aus der benutzerdefinierte färbbare Elemente-Enumeration, die von der Parser oder Scanner zurückgegebenen Tokentypen entspricht.  
  
5.  In der gleichen Klasse, die implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Schnittstelle und über zwei Methoden, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>-Schnittstelle.  
  
7.  Wenn Sie 24-Bit- oder hohe Farbwerte unterstützen möchten, implementieren Sie außerdem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle.  
  
8.  Erstellen Sie in das Dienstobjekt Sprache eine Liste mit Ihrer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Objekten, eines für jedes färbbare Element den Parser oder Scanner identifizieren kann.  
  
     Sie können jedes Element in der Liste mit den entsprechenden Wert aus der Enumeration benutzerdefinierte färbbare Elemente zugreifen. Verwenden Sie die Enumerationswerte als Index in der Liste. Das erste Element in der Liste nie zugegriffen wird, da er den Standardtext entspricht ein Format zuzuweisen, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] immer selbst behandelt. Sie können dafür kompensiert werden durch einen Platzhalter färbbare Element am Anfang der Liste einfügen.  
  
9. In der Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> -Methode, die Anzahl der Elemente in der Liste Ihrer benutzerdefinierte färbbare Elemente zurück.  
  
10. In der Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> -Methode, die angeforderte färbbare Element aus der Liste zurückgeben.  
  
 Ein Beispiel zum Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstellen, finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Modell von einem Legacy-Sprachdienst](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Syntaxfarben in einen Legacy-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren die Farben für Syntax](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)