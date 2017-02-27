---
title: "Benutzerdefinierte F&#228;rbbare Elemente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "färbbare Elemente"
  - "Language Services, benutzerdefinierte färbbare Elemente"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Benutzerdefinierte F&#228;rbbare Elemente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können die Liste der Typen überschreiben implementieren benutzerdefinierte färbbare Elemente als Teil der Sprachdienst für die farbliche Kennzeichnung, z. B. Schlüsselwörter und Kommentare.  
  
## Benutzereinstellungen Färbbare Elemente  
 Anzeigen der **Schriftarten und Farben** Dialogfeld dazu **Optionen** auf der **Tools** Menü, und wählen Sie dann **Schriftarten und Farben** unter **Umgebung**. Bei der Auswahl einer Anzeige, wie z. B. **Text\-Editor** oder **Befehlsfenster**,  **Elemente anzeigen** im Listenfeld werden alle färbbare Elemente für zur Anzeige. Sie können anzeigen und ändern die Schriftart, Größe, Vordergrundfarbe und Hintergrundfarbe für jede färbbare Element. Ihre Auswahl in einem Cache in der Registrierung gespeichert und mit dem Namen färbbare Element zugegriffen.  
  
## Darstellung der Färbbare Elemente  
 Da die IDE Benutzer überschreibt der färbbare Elemente in behandelt die **Schriftarten und Farben** Dialogfeld müssen Sie nur jede benutzerdefiniertes färbbare Element mit einem Namen angeben. Dieser Name wird in der **Elemente anzeigen** Liste. Die färbbare Elemente werden in alphabetischer Reihenfolge. Um des Sprachdiensts benutzerdefinierte färbbare Elemente zu gruppieren, können Sie z. B. den Namen durch den Sprachnamen Ihres beginnen **NewLanguage \- Kommentar** und **NewLanguage \- Schlüsselwort**.  
  
> [!CAUTION]
>  Name der Sprache aufzunehmen im Namen färbbare Element zum Vermeiden von Konflikten mit vorhandenen Namen von färbbare Element. Wenn Sie den Namen eines färbbare Elemente während der Entwicklung ändern, müssen Sie den Cache zurücksetzen, der Ihre färbbare Artikel zugegriffen wurde erstmalig erstellt wurde. Sie können die experimentellen Cache mit dem Tool CreateExpInstance Zurücksetzen der mit Visual Studio SDK, in der Regel im Verzeichnis installiert wird  
>   
>  **C:\\Programme\\Microsoft Dateien \(x86\) \\Microsoft Visual Studio 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  Um den Cache zurückzusetzen, rufen Sie `CreateExpInstance /Reset`. Weitere Informationen zu CreateExpInstance, finden Sie unter [CreateExpInstance\-Dienstprogramm](../../extensibility/internals/createexpinstance-utility.md).  
  
 Das erste Element in der Liste der färbbare Elemente wird nicht verwiesen. Das erste Element entspricht einem färbbare Elementindex 0 und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt immer die Standardfarben für Text und die Attribute für dieses Element. Die einfachste Möglichkeit für den Umgang mit diesem nicht referenzierte Element ist ein Platzhalter färbbare Element in der Liste als erstes Element angeben.  
  
## Implementieren benutzerdefinierte Färbbare Elemente  
  
1.  Definieren Sie, was in Ihrer Sprache, z. B. Schlüsselwort, Operator und Bezeichner farbig hervorgehoben werden muss.  
  
2.  Erstellen Sie eine Enumeration färbbare Elemente.  
  
3.  Ordnen Sie die Typen die token von Parser oder Scanner mit den aufgelisteten Werten zurückgegeben.  
  
     Die Werte, die die Tokentypen darstellt konnte z. B. die gleichen Werte in der Enumeration benutzerdefinierte färbbare Elemente sein.  
  
4.  In der Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> \-Methode in Ihrer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Objekt, füllen Sie die Liste der Attribute mit den Werten aus der benutzerdefinierte färbbare Elemente\-Enumeration, die von der Parser oder Scanner zurückgegebenen Tokentypen entspricht.  
  
5.  In der gleichen Klasse, die implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> \-Schnittstelle und die beiden Methoden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>\-Schnittstelle.  
  
7.  Wenn Sie die 24\-Bit\- oder hohe Farbwerte unterstützen möchten, implementieren Sie außerdem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle.  
  
8.  Erstellen Sie in Ihrer Sprache Service\-Objekt, eine Liste mit Ihrer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Objekten, eines für jedes färbbare Element der Parser oder Scanner identifizieren kann.  
  
     Sie können jedes Element in der Liste mit den entsprechenden Wert aus der Enumeration benutzerdefinierte färbbare Elemente zugreifen. Verwenden Sie die Enumerationswerte als Index in der Liste. Das erste Element in der Liste nie zugegriffen wird, da es den Standardtext entspricht zu formatieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] immer selbst behandelt. Sie können für diese kompensieren, durch einen Platzhalter färbbare Element am Anfang der Liste einfügen.  
  
9. In der Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> \-Methode, die Anzahl der Elemente in der Liste benutzerdefinierte färbbare Elemente zurück.  
  
10. Die Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> \-Methode, das angeforderte färbbare Element aus der Liste zurück.  
  
 Ein Beispiel zum Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> \-Schnittstellen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## Siehe auch  
 [Modell eines Legacy\-Language\-Diensts](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Syntaxfarben in eine Legacy\-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Farben für Syntax](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Gewusst wie: Verwenden von integrierten Färbbare Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)