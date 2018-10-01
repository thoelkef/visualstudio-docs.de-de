---
title: Unterstützung für die Navigationsleiste in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e62ac19a42877c1c7c995ffd3d416b5225514b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522979"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Unterstützen der Navigationsleiste in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Unterstützung für die Navigationsleiste in einem Legacysprachdienst](https://docs.microsoft.com/visualstudio/extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service).  
  
Die Navigationsleiste am oberen Rand die Editor-Ansicht zeigt die Typen und Member in der Datei an. Typen werden angezeigt, in der linken Dropdownliste aus, und Elemente werden in der rechten Dropdownliste angezeigt. Wenn der Benutzer einen Typ auswählt, wird die Einfügemarke in der ersten Zeile des Typs platziert. Wenn der Benutzer ein Element auswählt, wird die Einfügemarke in die Definition des Elements platziert. Die Dropdown-Felder werden entsprechend die aktuelle Position der Einfügemarke aktualisiert.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Anzeigen und aktualisieren die Navigationsleiste  
 Um die Navigationsleiste unterstützen zu können, müssen Sie leiten eine Klasse von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse und Implementieren der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode. Wenn erhält der Sprachdienst einem Code-Fenster, die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse instanziiert die <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, enthält die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Objekt, das im Code-Fenster darstellt. Die <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Objekt erhält dann eine neue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt. Die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode ruft eine <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt. Wenn Sie eine Instanz des zurückzugeben Ihre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> -Klasse, die <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Aufrufe Ihrer <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode, um die interne Auffüllen aufgelistet und übergibt Ihre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> -Objekt an die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dropdown-Leiste Manager. Der Dropdown-bar-Manager wiederum ruft die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> Methode für Ihre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt, das Einrichten der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> -Objekt, die zwei dropdownleisten enthält.  
  
 Wenn die Einfügemarke verschoben wird, die <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methode. Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> -Methode in Ihrer <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse, um den Status der Navigationsleiste zu aktualisieren. Übergeben Sie einen Satz von <xref:Microsoft.VisualStudio.Package.DropDownMember> Objekte für diese Methode. Jedes Objekt stellt einen Eintrag in der Dropdownliste aus.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Der Inhalt der Navigationsleiste  
 Die Navigationsleiste in der Regel enthält eine Liste von Typen und eine Liste von Elementen. Die Liste der Typen enthält alle verfügbaren Typen in der aktuellen Quelldatei. Die Typnamen enthalten den vollständigen Namespace-Informationen. Im folgenden finden ein Beispiel für C#-Code mit zwei Typen:  
  
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
  
 Die Liste zeigt `TestLanguagePackage.TestLanguageService` und `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Die Liste Elemente zeigt die verfügbaren Mitglieder des Typs, der in der Liste der Typen ausgewählt ist. Im obigen Codebeispiel zu verwenden, wenn `TestLanguagePackage.TestLanguageService` ist der Typ, der ausgewählt wird, enthält die Mitgliederliste die privaten Member `tokens` und `serviceName`. Die interne Struktur `Token` wird nicht angezeigt.  
  
 Sie können die Memberliste, um den Namen eines Members fett formatieren, wenn die Einfügemarke in die Datei platziert wird, implementieren. Mitglieder können auch in angezeigt werden abgeblendeter Text, gibt an, dass sie nicht innerhalb des Bereichs sind, in dem die Einfügemarke positioniert ist.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Aktivieren der Unterstützung für die Navigationsleiste  
 Um Unterstützung für die Navigationsleiste aktivieren, müssen Sie festlegen der `ShowDropdownBarOption` Parameter, der die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attribut `true`. Dieser Parameter legt die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>-Eigenschaft fest. Sie müssen zur Unterstützung der Navigationsleiste implementieren die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> -Objekt in der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 In der Implementierung von der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> -Methode, wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> -Eigenschaftensatz auf `true`, kann man eine <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt. Wenn Sie nicht das Objekt zurückgeben, wird die Navigationsleiste nicht angezeigt.  
  
 Die Option zum Anzeigen der Navigationsleiste kann vom Benutzer festgelegt werden, daher ist es möglich, dass dieses Steuerelement zurückgesetzt werden, während die Editor-Ansicht geöffnet ist. Der Benutzer muss schließen und öffnen im Editor-Fenster aus, bevor die Änderung in Kraft tritt.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementieren der Unterstützung für die Navigationsleiste  
 Die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> -Methode übernimmt zwei Listen (eine für jede Dropdown-Liste) und zwei Werte, die die aktuelle Auswahl in jeder Liste darstellt. Die Listen und die Auswahlwerte können aktualisiert werden, in diesem Fall die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methodenrückgabewert müssen `true` , um anzugeben, dass die Listen geändert haben.  
  
 Wenn die Auswahl in der Dropdown-Typen geändert wird, muss die Mitgliederliste aktualisiert werden, entsprechend den neuen Typ. Was in der Liste angezeigt wird, kann Folgendes sein:  
  
-   Die Liste der Mitglieder für den aktuellen Typ.  
  
-   Alle Member verfügbar im Quell-Datei, aber mit allen Elementen nicht im aktuellen Typ, der in abgeblendeten Text angezeigt. Der Benutzer auswählen kann immer noch die Elemente ausgegraut ist, daher sie für die schnelle Navigation verwendet werden können, aber die Farbe Gibt an, dass sie nicht Teil des ausgewählten Typs sind.  
  
 Eine Implementierung der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode in der Regel führt die folgenden Schritte aus:  
  
1.  Ruft eine Liste der aktuellen Deklarationen für die Quelldatei.  
  
     Es gibt eine Reihe von Möglichkeiten zum Auffüllen der Listen. Ein Ansatz besteht darin, erstellen Sie eine benutzerdefinierte Methode in Ihrer Version von der <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse, die Aufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode mit einem Grund für die benutzerdefinierte Analyse, die eine Liste mit allen Deklarationen zurückgibt. Ein anderer Ansatz ist möglicherweise rufen Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode direkt aus der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode mit dem Grund für die benutzerdefinierte Analyse. Ein dritter Ansatz ist möglicherweise die Deklarationen in den cache der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, die von der letzten vollständigen Analysevorgang in zurückgegebenen der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und abzurufen, die von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode.  
  
2.  Füllen Sie auf und aktualisieren Sie die Liste der Typen.  
  
     Der Inhalt der Liste der Typen sollten aktualisiert werden, wenn die Quelle geändert hat oder wenn Sie ausgewählt haben, so ändern Sie den Textstil der Typen basierend auf der aktuellen Position der Einfügemarke. Diese Position übergeben, um die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode.  
  
3.  Bestimmen Sie den Typ, wählen Sie in der Liste der Typen basierend auf der aktuellen Position der Einfügemarke ein.  
  
     Sie können Suchen in Schritt 1 fest, um den Typ zu suchen, der von der aktuellen Position der Einfügemarke enthält, Deklarationen, die abgerufen wurden und suchen Sie dann die Liste der Typen für diesen Typ, dessen Index in der Liste der Typen zu ermitteln.  
  
4.  Füllen Sie auf und aktualisieren Sie die Liste der Mitglieder basierend auf den ausgewählten Typ.  
  
     Die Mitgliederliste spiegelt wider, was derzeit angezeigt wird, in der **Mitglieder** Dropdown-Liste. Der Inhalt der Liste Elemente müssen möglicherweise aktualisiert werden, wenn die Quelle geändert hat, oder Sie werden nur die Elemente des ausgewählten Typs angezeigt, und der ausgewählte Typ geändert wurde. Wenn Sie alle Elemente in der Quelldatei angezeigt, auch und klicken Sie dann der Textstil für jedes Elements in der Liste muss aktualisiert werden, wenn der aktuell ausgewählte Typ geändert wurde.  
  
5.  Bestimmen Sie das Element, wählen Sie in der Liste der Mitglieder basierend auf der aktuellen Position der Einfügemarke ein.  
  
     Suchen Sie die Deklarationen, die abgerufen wurden in Schritt 1, für das Element, das der aktuellen Position der Einfügemarke enthält, und suchen Sie die Liste der Elemente für dieses Element aus, um zu bestimmen, dessen Index in der Memberliste aus.  
  
6.  Zurückgeben `true` Wenn Änderungen in den Listen oder die Auswahl in einer der Listen vorgenommen wurden.

