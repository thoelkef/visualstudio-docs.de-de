---
title: "Unterst&#252;tzung f&#252;r die Navigationsleiste in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Navigationsleiste, Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "Sprachdienste [Verwaltetes Paketframework], Navigationsleiste"
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Unterst&#252;tzung f&#252;r die Navigationsleiste in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Navigationsleiste am oberen Rand der Editoransicht sind die Typen und Member in der Datei an.  Typen werden im linken Dropdownliste angezeigt, und Member werden im rechten Dropdownliste angezeigt.  Wenn der Benutzer einen Typ ausgewählt wird, wird die Einfügemarke in die erste Zeile des Typs platziert.  Wenn der Benutzer einen Member auswählt, wird die Einfügemarke in die Definition des Members gespeichert.  Die Dropdownfelder werden aktualisiert, um den aktuellen Position der Einfügemarke zu entsprechen.  
  
## Die Navigationsleiste anzeigen und Aktualisieren  
 Um die Navigationsleiste zu unterstützen, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Klasse ableiten und die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode implementieren.  Wenn der Sprachdienst ein Codefenster angegeben ist, instanziiert die Basis <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, die das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>\-Objekt, das das Codefenster darstellt.  Das Objekt ist <xref:Microsoft.VisualStudio.Package.CodeWindowManager> dann ein neues <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>\-Objekt angegeben.  Die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>\-Methode ruft ein <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Objekt ab.  Wenn Sie eine Instanz der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Klasse zurückgeben, ruft <xref:Microsoft.VisualStudio.Package.CodeWindowManager> die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode auf, um die internen Listen gefüllt und übergibt das <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Objekt mit dem Dropdownfeld Leiste [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Manager.  Der Dropdownliste Leiste Manager ruft wiederum die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>\-Methode auf dem <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Objekt an, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> Objekt festzulegen, das die beiden Dropdownliste Balken enthält.  
  
 Wenn sich die Einfügemarke befindet, die <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>\-Methode ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>\-Methode.  Die Basis\- <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>\-Methode ruft die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Klasse, um den Zustand der Navigationsleiste zu aktualisieren.  Sie führen einen Satz von <xref:Microsoft.VisualStudio.Package.DropDownMember>\-Objekte an diese Methode.  Jedes Objekt stellt einen Eintrag in der Dropdownliste dar.  
  
## Der Inhalt der Navigationsleiste  
 Die Navigationsleiste enthält normalerweise eine Liste von Typen und einer Liste von Membern.  Die Liste der Typen umfasst alle Typen, die in der aktuellen Quelldatei verfügbar sind.  Die Namespaceinformationen die vollständigen Typnamen enthalten.  Im Folgenden finden Sie ein Beispiel für C\#\-Code mit zwei Typen:  
  
```c#  
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
  
 Die Liste Typ wird `TestLanguagePackage.TestLanguageService` und `TestLanguagePackage.TestLanguageService.Tokens`an.  
  
 In der Memberliste werden die verfügbaren Member des Typs an, der in der Liste Typ ausgewählt wird.  Verwenden des Codebeispiels oben, wenn der Typ ist, der `TestLanguagePackage.TestLanguageService` ausgewählt ist, wird die Memberliste die privaten Member `tokens` und `serviceName`enthalten.  Die interne Struktur `Token` wird nicht angezeigt.  
  
 Sie können die Liste Member implementieren, um den Namen eines Members fett zu gestalten, wenn die Einfügemarke innerhalb der platziert wird.  Member können auch im abgeblendeten Text angezeigt und angeben, dass sie nicht innerhalb des Bereichs liegen, in dem das Caretzeichen gerade positioniert ist.  
  
## Unterstützung für die Navigationsleiste aktivieren  
 Zur Unterstützung der Navigationsleiste zu aktivieren, müssen Sie den `ShowDropdownBarOption`\-Parameter des Attributs <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>`true`festlegen.  Mit diesem Parameter wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>\-Eigenschaft festgelegt.  Um die Navigationsleiste zu unterstützen, müssen Sie das <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Objekt in der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>\-Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse implementieren.  
  
 In der Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>\-Methode, wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>\-Eigenschaft auf `true`festgelegt ist, können Sie ein <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Objekt zurückgeben.  Wenn Sie nicht das Objekt zurückgeben, wird die Navigationsleiste nicht angezeigt.  
  
 Die Option, um die Navigationsleiste angezeigt werden kann vom Benutzer festgelegt wurden. Daher ist es für dieses Steuerelement zurückgesetzt werden, während die Editoransicht geöffnet ist.  Der Benutzer muss das Editorfenster schließen und erneut öffnen, bevor die Änderung ausgeführt wird.  
  
## Unterstützung für die Navigationsleiste implementieren  
 Die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode akzeptiert zwei Listen \(eine für jede Dropdownliste\) und zwei Werten, das die aktuelle Auswahl in jeder Liste darstellen.  Die Listen und die Auswahl von Werten können aktualisiert werden. In diesem Fall wird die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode `true` zurückgeben muss, um anzugeben, dass die Listen geändert haben.  
  
 Während sich die Auswahl ändert, muss in der Dropdownliste Typ in der Memberliste werden aktualisiert, um den neuen Typ wiederzugeben.  Was in der Memberliste angezeigt wird, können entweder:  
  
-   Die Liste der Member für den aktuellen Typ.  
  
-   Alle Member verfügbar in der Quelldatei, aber mit allen Membern nicht im aktuellen Typ angezeigt im abgeblendeten Text.  Der Benutzer kann die abgeblendeten weiterhin Member auswählen, sodass sie für die schnelle Navigation verwendet werden, aber die Farbe gibt an, dass sie nicht Teil des aktuell ausgewählten Typs sind.  
  
 Eine Implementierung der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode wird i. d. R. die folgenden Schritte aus:  
  
1.  Rufen Sie eine Liste der aktuellen Deklarationen für die Quelldatei ab.  
  
     Es gibt verschiedene Möglichkeiten, die Listen aufzufüllen.  Ein Ansatz besteht darin, eine benutzerdefinierte Methode auf der Version der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse erstellen, die die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode mit einem benutzerdefinierten Analyse grund aufruft, der eine Liste aller Deklarationen zurückgibt.  Ein anderer Ansatz kann, die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode direkt von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode mit dem benutzerdefinierten Analyse grund aufzurufen.  Ein dritter Ansatz kann, Deklarationen in der <xref:Microsoft.VisualStudio.Package.AuthoringScope>\-Klasse zwischenspeichern, die vom letzten vollständigen Analysevorgang in der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse und das Abrufen von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode zurückgegeben wird.  
  
2.  Füllen Sie auf oder aktualisieren Sie die Liste von primitiven Typen.  
  
     Der Inhalt der Liste Typ aktualisiert werden kann, wenn die Quelle geändert wurde, oder wenn Sie ausgewählt haben, dass der Text formatieren die Typen auf Grundlage der aktuellen Position der Einfügemarke zu ändern.  Beachten Sie, dass diese Position in die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode übergeben wird.  
  
3.  Bestimmen Sie den Typ, um in der Liste Typ auf der aktuellen Position der Einfügemarke auszuwählen.  
  
     Sie können die Deklarationen finden, die in Schritt 1 erhalten, um den Typ zu suchen, der die aktuelle Position der Einfügemarke einschließt, und dann die Liste Typ gefunden wurden, sodass dieser Typ über seinen Index in der Liste Typ bestimmt.  
  
4.  Füllen Sie auf oder aktualisieren Sie die Liste der Member auf Grundlage des ausgewählten Typs.  
  
     Die Memberliste aus, was derzeit im **Member** Dropdownpfeil angezeigt wird.  Der Inhalt der Memberliste müssen möglicherweise aktualisiert werden, wenn die Quelle geändert hat oder wenn Sie nur die Member des ausgewählten Typs und des ausgewählten Typs angezeigt werden, geändert wurden.  Wenn Sie alle Member in der Quelldatei anzuzeigen, muss das Text formatieren jedes Members in der Liste aktualisiert werden, wenn der aktuell ausgewählten Typs geändert hat.  
  
5.  Bestimmen Sie den Member, der in der Memberliste auf Grundlage der aktuellen Position der Einfügemarke auszuwählen.  
  
     Suchen Sie die Deklarationen, die in Schritt 1 für den Member erhalten, der die aktuelle Position der Einfügemarke enthält, die Memberliste gefunden wurden, sodass dieser Member den Index in der Memberliste bestimmt.  
  
6.  Geben Sie `true` , wenn Änderungen wurden an den Listen oder Auswahl in jeder Liste vorgenommen.