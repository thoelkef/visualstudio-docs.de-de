---
title: "Unterstützung für die Navigationsleiste in einen Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: eb5212c4828ad24256447bc1c75f85ec0d9d9579
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Unterstützung für die Navigationsleiste in einen Legacy-Sprachdienst
Die Navigationsleiste am oberen Rand der Editor-Ansicht zeigt die Typen und Member in der Datei an. Typen in der linken Dropdownliste angezeigt werden, und Elemente werden in der rechten Dropdownliste angezeigt. Wenn der Benutzer einen Typ auswählt, wird das Caretzeichen auf der ersten Zeile des Typs platziert. Wenn der Benutzer ein Element auswählt, wird das Caretzeichen auf der Definition des Elements eingefügt. Die Dropdown-Felder werden entsprechend die aktuelle Position des Caretzeichens aktualisiert.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Anzeigen und aktualisieren die Navigationsleiste  
 Unterstützung die Navigationsleiste, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse und Implementieren der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode. Wenn Ihre Sprachdienst erhält ein Codefenster, der Base <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse instanziiert die <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, enthält die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> -Objekt, das Code-Fenster darstellt. Die <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Objekt erhält dann ein neues <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt. Die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode ruft eine <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt. Bei Rückgabe eine Instanz von Ihrer <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> -Klasse, die <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Aufrufe Ihrer <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode zum Auffüllen der internen aufgelistet und übergibt Ihre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> -Objekt an die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dropdownelement Strich Manager. Der Dropdown-Strich-Manager wiederum die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> Methode für Ihre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt zum Herstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> Objekt, das die zwei Dropdownlisten enthält.  
  
 Wenn die Einfügemarke bewegt wird, die <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methode. Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode in Ihrer <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse, um den Zustand der Navigationsleiste zu aktualisieren. Übergeben Sie einen Satz von <xref:Microsoft.VisualStudio.Package.DropDownMember> Objekte an diese Methode. Jedes Objekt repräsentiert einen Eintrag in der Dropdownliste aus.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Der Inhalt der Navigationsleiste  
 Die Navigationsleiste in der Regel enthält eine Liste von Typen und eine Liste von Elementen. Die Liste der Typen enthält alle verfügbaren Typen in der aktuellen Quelldatei. Die vollständige Namespaceinformationen einschließen des Typennamens Im folgenden finden ein Beispiel für C#-Code mit zwei Typen:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Zeigt die Liste der `TestLanguagePackage.TestLanguageService` und `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Die Mitgliederliste zeigt die verfügbaren Elemente des Typs, der in der Liste ausgewählt ist. Verwenden im Codebeispiel oben, wenn `TestLanguagePackage.TestLanguageService` der Typ, der aktiviert ist, wird der Mitgliederliste würde die privaten Member enthalten `tokens` und `serviceName`. Die interne Struktur `Token` wird nicht angezeigt.  
  
 Sie können die Memberliste, um den Namen eines Members fett, wenn die Einfügemarke, darin platziert wird implementieren. Mitglieder können auch in angezeigt werden abgeblendet Text, der angibt, dass sie nicht innerhalb des Bereichs sind, wo der Textcursor gerade positioniert ist.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Aktivieren der Unterstützung für die Navigationsleiste  
 Um die Unterstützung für die Navigationsleiste aktivieren, müssen Sie festlegen der `ShowDropdownBarOption` Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> -Attribut auf `true`. Dieser Parameter legt die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>-Eigenschaft fest. Sie müssen zur Unterstützung der Navigationsleiste implementieren die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt in der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode auf die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 In der Implementierung von der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> -Methode, wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> -Eigenschaftensatz auf `true`, können Sie zurückkehren, eine <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt. Wenn Sie nicht das Objekt zurückgeben, wird die Navigationsleiste nicht angezeigt.  
  
 Die Option zum Anzeigen der Navigationsleiste kann vom Benutzer festgelegt werden, daher ist es möglich, dass dieses Steuerelement zurückgesetzt werden sollen, während die Editor-Ansicht geöffnet ist. Der Benutzer muss schließen und öffnen im Editor-Fenster, bevor die Änderung stattfindet.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementieren der Unterstützung für die Navigationsleiste  
 Die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> -Methode übernimmt zwei Listen (eine für jede Dropdown-) und zwei Werte, die die aktuelle Auswahl in jeder Liste darstellt. Die Listen und die Auswahlwerte können aktualisiert werden, in diesem Fall die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methodenrückgabewert müssen `true` , um anzugeben, dass die Listen geändert wurden.  
  
 Da sich die Auswahl in der Dropdown-Typen ändern, muss die Mitgliederliste entsprechend den neuen Typ aktualisiert werden. In der Liste der angezeigten Optionen sind möglich:  
  
-   Die Liste der Mitglieder für den aktuellen Typ.  
  
-   Alle der verfügbaren Elemente in der Quelle der Datei, aber mit allen Elementen nicht im aktuellen Typ ausgegrautes Text angezeigt. Der Benutzer kann weiterhin die ausgegrautes Elemente auswählen, damit für die schnelle Navigation verwendet werden können, aber die Farbe Gibt an, dass sie nicht Teil des aktuell ausgewählten Typs sind.  
  
 Eine Implementierung der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode in der Regel führt die folgenden Schritte aus:  
  
1.  Ruft eine Liste der aktuellen Deklarationen für die Quelldatei.  
  
     Es gibt zahlreiche Möglichkeiten zum Auffüllen der Liste aus. Ein Ansatz besteht darin, erstellen Sie eine benutzerdefinierte Methode für Ihre Version von den <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse, die Aufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode mit einem benutzerdefinierten Analyse Grund, die eine Liste mit allen Deklarationen zurückgibt. Möglicherweise ein anderer Ansatz zum Aufrufen der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode direkt aus der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode mit dem Grund der benutzerdefinierten analysieren. Ein dritter Ansatz wäre, die Deklarationen in Zwischenspeichern der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, die von der letzten vollständigen Analysevorgang im zurückgegebenen den <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und abzurufen, die von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode.  
  
2.  Auffüllen von oder aktualisieren Sie die Liste der Typen.  
  
     Der Inhalt der Liste der Typen sollten aktualisiert werden, wenn die Quelle geändert hat oder wenn Sie ausgewählt haben, so ändern Sie den Textstil der Typen, die basierend auf der aktuellen Position der Einfügemarke. Beachten Sie, die an dieser Position der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode.  
  
3.  Bestimmen Sie den Typ in der Liste der Typen basierend auf der aktuellen Position der Einfügemarke auswählen.  
  
     Sie können Suchen in Schritt 1 fest, um den Typ zu suchen, der zur aktuellen CaretPosition umschließt Deklarationen, die abgerufen wurden, und suchen Sie dann die Liste der Typen für diesen Typ aus, um zu bestimmen, deren Index in der Liste der Typen.  
  
4.  Auffüllen von oder aktualisieren Sie die Liste der Elemente, die basierend auf dem ausgewählten Typ.  
  
     Die Mitgliederliste widerspiegelt, was derzeit in angezeigt wird der **Elemente** Dropdownliste aus. Der Inhalt der Memberliste müssen möglicherweise aktualisiert werden, wenn die Quelle geändert hat oder wenn Sie nur die Elemente des ausgewählten Typs anzeigen und der ausgewählte Typ geändert wurde. Wenn Sie auswählen, alle Elemente in der Quelldatei, und klicken Sie dann der Textstil für jedes Element in der Liste muss aktualisiert werden, wenn der aktuell ausgewählte Typ geändert wurde.  
  
5.  Bestimmen Sie das Element, wählen Sie in der Liste der Elemente basierend auf der aktuellen Position der Einfügemarke.  
  
     Suchen Sie die Deklarationen, die abgerufen wurden in Schritt 1 für das Element, das zur aktuellen CaretPosition enthält, und Durchsuchen Sie die Liste der Elemente für dieses Element aus, um zu bestimmen, deren Index in der Memberliste aus.  
  
6.  Zurückgeben `true` , wenn die Listen oder die Auswahl in einer der Listen Änderungen vorgenommen wurden.
