---
title: Unterstützung für die Navigationsleiste in einem Legacy Language Service | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704861"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Unterstützen der Navigationsleiste in einem Legacysprachdienst
In der Navigationsleiste oben in der Editoransicht werden die Typen und Elemente in der Datei angezeigt. Typen werden in der linken Dropdownliste und Member in der rechten Dropdownliste angezeigt. Wenn der Benutzer einen Typ auswählt, wird die Einstellte in der ersten Zeile des Typs platziert. Wenn der Benutzer ein Element auswählt, wird die Einsersorge auf die Definition des Elements gelegt. Die Dropdown-Felder werden aktualisiert, um den aktuellen Speicherort der Einstelle widerzuspiegeln.

## <a name="displaying-and-updating-the-navigation-bar"></a>Anzeigen und Aktualisieren der Navigationsleiste
 Um die Navigationsleiste zu unterstützen, müssen <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Sie eine <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Klasse aus der Klasse ableiten und die Methode implementieren. Wenn Ihrem Sprachdienst ein Codefenster <xref:Microsoft.VisualStudio.Package.LanguageService> angezeigt wird, instanziiert die Basisklasse die <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, die das Objekt enthält, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> das Codefenster darstellt. Dem <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Objekt wird dann <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ein neues Objekt gegeben. Die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ruft ein Objekt ab. Wenn Sie eine Instanz <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Ihrer <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Klasse <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> zurückgeben, ruft die Methode zum <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Auffüllen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der internen Listen auf und übergibt das Objekt an den Dropdown-Bar-Manager. Der Dropdown-Balken-Manager ruft wiederum <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Methode für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> das Objekt auf, um das Objekt einzurichten, das die beiden Dropdown-Balken enthält.

 Wenn sich die Einserart bewegt, ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Methode die <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methode auf. Die <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Basismethode <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> ruft die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Methode in Ihrer Klasse auf, um den Status der Navigationsleiste zu aktualisieren. Sie übergeben eine <xref:Microsoft.VisualStudio.Package.DropDownMember> Reihe von Objekten an diese Methode. Jedes Objekt stellt einen Eintrag in der Dropdown-Liste dar.

## <a name="the-contents-of-the-navigation-bar"></a>Der Inhalt der Navigationsleiste
 Die Navigationsleiste enthält in der Regel eine Liste von Typen und eine Liste von Elementen. Die Liste der Typen enthält alle Typen, die in der aktuellen Quelldatei verfügbar sind. Die Typnamen enthalten die vollständigen Namespaceinformationen. Im Folgenden finden Sie ein Beispiel für C-Code mit zwei Typen:

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

 Die Typliste `TestLanguagePackage.TestLanguageService` wird `TestLanguagePackage.TestLanguageService.Tokens`angezeigt und .

 In der Mitgliederliste werden die verfügbaren Member des Typs angezeigt, der in der Typenliste ausgewählt ist. Wenn es sich bei `TestLanguagePackage.TestLanguageService` dem oben beschriebenen Codebeispiel um den `tokens` ausgewählten `serviceName`Typ handelt, enthält die Mitgliederliste die privaten Member und . Die interne `Token` Struktur wird nicht angezeigt.

 Sie können die Mitgliederliste implementieren, um den Namen eines Mitglieds fett zu machen, wenn die Einstellte darin platziert wird. Mitglieder können auch in abgeblendetem Text angezeigt werden, was darauf hinweist, dass sie sich nicht innerhalb des Bereichs befinden, in dem sich die Einstellte gerade befindet.

## <a name="enabling-support-for-the-navigation-bar"></a>Aktivieren der Unterstützung für die Navigationsleiste
 Um die Unterstützung für die Navigationsleiste `ShowDropdownBarOption` zu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> aktivieren, `true`müssen Sie den Parameter des Attributs auf festlegen. Dieser Parameter legt die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>-Eigenschaft fest. Um die Navigationsleiste zu unterstützen, müssen Sie das <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt in der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse implementieren.

 Wenn <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Eigenschaft in der Implementierung der `true`Methode auf <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> festgelegt ist, können Sie ein Objekt zurückgeben. Wenn Sie das Objekt nicht zurückgeben, wird die Navigationsleiste nicht angezeigt.

 Die Option zum Anzeigen der Navigationsleiste kann vom Benutzer festgelegt werden, sodass dieses Steuerelement zurückgesetzt werden kann, während die Editoransicht geöffnet ist. Der Benutzer muss das Editorfenster schließen und erneut öffnen, bevor die Änderung stattfindet.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementieren der Unterstützung für die Navigationsleiste
 Die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode verwendet zwei Listen (eine für jede Dropdownliste) und zwei Werte, die die aktuelle Auswahl in jeder Liste darstellen. Die Listen und die Selektionswerte <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> können aktualisiert `true` werden, in diesem Fall muss die Methode zurückkehren, um anzugeben, dass sich die Listen geändert haben.

 Wenn sich die Auswahl in der Dropdownliste der Typen ändert, muss die Mitgliederliste aktualisiert werden, um den neuen Typ widerzuspiegeln. Was in der Mitgliederliste angezeigt wird, kann entweder sein:

- Die Liste der Member für den aktuellen Typ.

- Alle Elemente, die in der Quelldatei verfügbar sind, jedoch alle Elemente nicht im aktuellen Typ, die in abgeblendetem Text angezeigt werden. Der Benutzer kann weiterhin die ausgegrauten Elemente auswählen, sodass sie für die schnelle Navigation verwendet werden können, aber die Farbe zeigt an, dass sie nicht Teil des aktuell ausgewählten Typs sind.

  Eine Implementierung <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> der Methode führt in der Regel die folgenden Schritte aus:

1. Abrufen einer Liste aktueller Deklarationen für die Quelldatei.

     Es gibt eine Reihe von Möglichkeiten, die Listen aufzufüllen. Ein Ansatz besteht darin, eine benutzerdefinierte <xref:Microsoft.VisualStudio.Package.LanguageService> Methode für <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Ihre Version der Klasse zu erstellen, die die Methode mit einem benutzerdefinierten Analysegrund aufruft, der eine Liste aller Deklarationen zurückgibt. Ein anderer Ansatz könnte <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> darin bestehen, die Methode direkt aus der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode mit dem benutzerdefinierten Analysegrund aufzurufen. Ein dritter Ansatz besteht möglicherweise darin, <xref:Microsoft.VisualStudio.Package.AuthoringScope> die Deklarationen in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse zwischenzuspeichern, die vom letzten vollständigen Analysevorgang in der Klasse zurückgegeben wurde, und diese aus der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode abzurufen.

2. Füllen oder aktualisieren Sie die Liste der Typen.

     Der Inhalt der Typenliste kann aktualisiert werden, wenn sich die Quelle geändert hat oder wenn Sie sich entschieden haben, die Textgestaltung der Typen basierend auf der aktuellen Einserposition zu ändern. Beachten Sie, dass diese <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Position an die Methode übergeben wird.

3. Bestimmen Sie den Typ, der in der Typenliste basierend auf der aktuellen Einserposition ausgewählt werden soll.

     Sie können die deklarationen durchsuchen, die in Schritt 1 abgerufen wurden, um den Typ zu finden, der die aktuelle Einsierposition umschließt, und dann die Typenliste nach diesem Typ durchsuchen, um seinen Index in der Typenliste zu bestimmen.

4. Füllen oder aktualisieren Sie die Liste der Mitglieder basierend auf dem ausgewählten Typ.

     Die Mitgliederliste gibt an, was derzeit in der Dropdown-Liste **Mitglieder** angezeigt wird. Der Inhalt der Mitgliederliste muss möglicherweise aktualisiert werden, wenn sich die Quelle geändert hat oder wenn Sie nur die Member des ausgewählten Typs anzeigen und der ausgewählte Typ geändert wurde. Wenn Sie alle Elemente in der Quelldatei anzeigen möchten, muss die Textgestaltung jedes Elements in der Liste aktualisiert werden, wenn sich der aktuell ausgewählte Typ geändert hat.

5. Bestimmen Sie das Mitglied, das in der Mitgliederliste basierend auf der aktuellen Einserposition ausgewählt werden soll.

     Durchsuchen Sie die Deklarationen, die in Schritt 1 für das Element abgerufen wurden, das die aktuelle Pflegeposition enthält, und durchsuchen Sie dann die Mitgliederliste nach diesem Mitglied, um seinen Index in der Mitgliederliste zu bestimmen.

6. Gibt `true` zurück, wenn Änderungen an den Listen oder der Auswahl in beiden Listen vorgenommen wurden.
