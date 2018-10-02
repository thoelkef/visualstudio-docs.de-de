---
title: Refactoring mit Umbenennen (c#) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a70293719a70b7d4029f5c563aff30466368e00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524923"
---
# <a name="rename-refactoring-c"></a>Umgestaltung durch Umbenennen (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Benennen Sie** ist ein refactoring Feature in der Visual Studio integrierte Entwicklungsumgebung (IDE), die eine einfache Möglichkeit zum Umbenennen der Bezeichner für Codesymbole wie Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen bereitstellt. **Benennen Sie** kann verwendet werden, um die Namen in den Kommentaren und Zeichenfolgen zu ändern und so ändern Sie die Deklarationen und Aufrufe eines Bezeichners.  
  
> [!NOTE]
>  Bei Verwendung der Quellcodeverwaltung für Visual Studio erhalten Sie die neueste Version von Quellen, bevor Sie versuchen, führen Sie die Umgestaltung mit Umbenennen.  
  
 Refactoring mit Umbenennung ist über die folgenden Visual Studio-Funktionen verfügbar:  
  
|Feature|Verhalten der Umgestaltung in der IDE|  
|-------------|----------------------------------------|  
|Code-Editor|Im Code-Editor, ist die Umgestaltung mit Umbenennen verfügbar, wenn Sie den Cursor auf bestimmte Arten von Codesymbolen zu positionieren. Wenn der Cursor in dieser Position befindet, können Sie Aufrufen der **umbenennen** Befehl über die Tastenkombination (STRG + R, STRG + R) oder durch Auswählen der **umbenennen** ein Smarttag, das oderimKontextmenüdenBefehl **Umgestalten** Menü.|  
|Klassenansicht|Wenn Sie einen Bezeichner in der Klassenansicht auswählen, refactoring mit Umbenennung ist im Kontextmenü verfügbar und **Umgestalten** Menü.|  
|Objektkatalog|Bei Auswahl ein Bezeichners im Objektkatalog refactoring mit Umbenennung ist nur verfügbar in der **Umgestalten** Menü.|  
|Das Eigenschaftenraster des Windows Forms-Designers|In der **Eigenschaftenraster** von der Windows Forms-Designer, ändern den Namen eines Steuerelements initiiert ein Umbenennungsvorgang für dieses Steuerelement. Die **umbenennen** wird das Dialogfeld nicht angezeigt.|  
|Projektmappen-Explorer|In **Projektmappen-Explorer**, **umbenennen** Befehl im Kontextmenü verfügbar ist. Wenn die ausgewählte Quelldatei eine Klasse enthält, deren Klassenname den Dateinamen entspricht, können Sie mit diesem Befehl gleichzeitig die Quelldatei umbenannt und Umgestaltung mit Umbenennen.<br /><br /> Z. B. Wenn Sie eine standardmäßige Windows-basierte Anwendung erstellen und benennen Sie um TestForm.cs "Form1.cs", der Name der Quelldatei "Form1.cs" ändert sich TestForm.cs und die Klasse Form1 und alle Verweise auf, dass die Klasse in TestForm umbenannt wird. **Hinweis:** der **Rückgängig** Befehl (STRG + Z) nur rückgängig machen, refactoring mit Umbenennung im Code und wird nicht geändert, die der Dateinamen an den ursprünglichen Namen. <br /><br /> Wenn die ausgewählte Quelldatei eine Klasse keinen enthält, deren Name dem Dateinamen entspricht, der **umbenennen** Befehl **Projektmappen-Explorer** nur die Quelldatei umbenannt und Umbenennen wird nicht ausgeführt Refactoring.|  
  
## <a name="rename-operations"></a>Umbenennen von Vorgängen  
 Beim Ausführen **umbenennen**, die umgestaltungs-Engine führt eine spezifische Umbenennungsvorgänge für jedes Symbol Code aus, wie in der folgenden Tabelle beschrieben.  
  
|Schlüsselsymbol|Umbenennungsvorgang|  
|-----------------|----------------------|  
|Feld|Ändert sich die Deklaration und Verwendungen des Felds in den neuen Namen ein.|  
|lokale variable|Ändert sich die Deklaration und Verwendung von Variablen in den neuen Namen ein.|  
|Methode|Ändert den Namen der Methode "und" alle Verweise auf diese Methode in den neuen Namen an. **Hinweis:** beim Umbenennen einer Erweiterungsmethode gibt der Umbenennungsvorgang für alle Instanzen der Methode, die im Bereich, unabhängig davon, ob die Erweiterungsmethode als statische Methode oder Instanzmethode verwendet wird. Weitere Informationen finden Sie unter [Erweiterungsmethoden](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Namespace|Ändert den Namen des Namespace in den neuen Namen in der Deklaration alle `using` Anweisungen und den vollqualifizierten Namen. **Hinweis:** beim Umbenennen eines Namespaces, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktualisiert auch die **Standard-Namespace** Eigenschaft für die **Anwendung** auf der Seite die **Projekt-Designer**. Diese Eigenschaft kann nicht zurückgesetzt werden, dazu **rückgängig machen** aus der **bearbeiten** Menü. Zurücksetzen der **Default Namespace** Eigenschaftswert, müssen Sie die Eigenschaft im Ändern der **Projekt-Designer**. Weitere Informationen finden Sie unter [Anwendungsseite](../ide/reference/application-page-project-designer-csharp.md).|  
|Eigenschaft|Ändert sich die Deklaration und Verwendung der Eigenschaft in den neuen Namen ein.|  
|Typ|Ändert sich alle Deklarationen und alle Verwendungen des Typs in den neuen Namen ein, z. B. Konstruktoren und Destruktoren. Für partielle Typen wird der Umbenennungsvorgang für alle Komponenten.|  
  
#### <a name="to-rename-an-identifier"></a>Um einen Bezeichner umbenennen  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `RenameIdentifier`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Platzieren Sie den Cursor auf `MethodB`, entweder in der Deklaration der Methode oder der Aufruf der Methode.  
  
3.  Von der **Umgestalten** , wählen Sie im Menü **umbenennen**. Die **umbenennen** Dialogfeld wird angezeigt.  
  
     Sie können auch mit der rechten Maustaste des Cursors, zeigen Sie auf **Umgestalten** auf das Kontextmenü, und klicken Sie dann auf **umbenennen** zum Anzeigen der **umbenennen** Dialogfeld.  
  
4.  In der **neuen Namen** Feld `MethodC`.  
  
5.  Wählen Sie die **in Kommentaren suchen** Kontrollkästchen.  
  
6.  Klicken Sie auf **OK**.  
  
7.  In der **Vorschau der Änderungen** Dialogfeld klicken Sie auf **übernehmen**.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>Um einen Bezeichner mit Smarttags umbenennen  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `RenameIdentifier`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  In der Deklaration für `MethodB`, oder geben Sie den Methodenbezeichner RÜCKTASTE. Unterhalb dieser Bezeichner ist eine Smarttag-Aufforderung erscheint.  
  
    > [!NOTE]
    >  Refactoring mit Umbenennung mit Smarttags bei der Deklaration eines Bezeichners kann nur aufgerufen werden.  
  
3.  Geben Sie die Tastenkombination UMSCHALT + ALT + F10, und drücken Sie dann auf den Pfeil nach unten der Smarttag-Menü angezeigt werden soll.  
  
     - oder -   
  
     Zeigen Sie den Mauszeiger auf die Smarttag-Eingabeaufforderung auf das Smarttag angezeigt werden soll. Klicken Sie dann den Mauszeiger auf das Smarttag, und klicken Sie auf den Pfeil nach unten, um die Smarttag-Menü angezeigt werden soll.  
  
4.  Wählen Sie die **umbenennen "\<identifer1 >', '\<Bezeichner2 >"** Menüelement zum Aufrufen der Umgestaltung mit Umbenennen ohne eine Vorschau der Änderungen an Ihrem Code. Alle Verweise auf  **\<identifer1 >** werden automatisch aktualisiert werden, um  **\<Bezeichner2 >**.  
  
     - oder -   
  
     Wählen Sie die **Vorschau benennen** Menüelement aufzurufende refactoring mit Umbenennung mit einer Vorschau der Änderungen an Ihrem Code. Die **Vorschau der Änderungen** Dialogfeld wird angezeigt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="renaming-implemented-or-overridden-members"></a>Umbenennen von implementiert oder überschriebene Member  
 Wenn Sie **umbenennen** ein Member, die implementiert/Außerkraftsetzungen oder wird von Mitgliedern in anderen Typen implementiert oder überschrieben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zeigt ein Dialogfeld mit dem Text, der Umbenennungsvorgang führt dazu, dass updateweitergaben an. Wenn Sie auf **Weiter**, die umgestaltungs-Engine-rekursiv findet und benennt Sie alle Member in Basis- und abgeleiteten Typen, die implementiert/Außerkraftsetzungen Beziehungen mit dem Element, das umbenannt wird.  
  
 Das folgende Codebeispiel enthält Member mit implementiert/Außerkraftsetzungen Beziehungen.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 Im vorherigen Beispiel umbenennen `C.Method()` auch benennt `Ibase.Method()` da `C.Method()` implementiert `Ibase.Method()`. Als Nächstes das Umgestaltungsmodul erkennt, dass `Ibase.Method()` wird implementiert, indem `Derived.Method()` und benennt `Derived.Method()`. Die Engine für Refactoring, nicht umbenannt `Base.Method()`, da `Derived.Method()` überschreibt nicht die `Base.Method()`. Die umgestaltungs-Engine wird hier beendet, es sei denn, Sie haben **umbenennen Überladungen** eingecheckt der **umbenennen** Dialogfeld.  
  
 Wenn **Überladungen umbenennen** aktiviert ist, benennt die Refactor-Engine `Derived.Method(int i)` überlädt `Derived.Method()`, `Base.Method(int i)` , da sie von außer Kraft gesetzt wird `Derived.Method(int i)`, und `Base.Method()` da es sich um eine Überladung der handelt. `Base.Method(int i)`.  
  
> [!NOTE]
>  Wenn Sie ein Element, die in einer referenzierten Assembly definiert wurde umbenennen, erklärt ein Dialogfeld an, dass es sich bei Umbenennung Erstellungsfehlern führen.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Durch Umbenennen der Eigenschaften von anonymen Typen  
 Wenn Sie eine Eigenschaft in anonymen Typen umbenennen, werden die Eigenschaften in anderen anonymen Typen Umbenennungsvorgang, die die gleichen Eigenschaften verfügen. Die folgenden Beispiele veranschaulichen dieses Verhalten.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Im vorangehenden Code umbenennen `ID` ändert `ID` in beide Anweisungen, da sie die gleichen zugrunde liegenden anonymen Typ haben.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Im vorangehenden Code umbenennen `ID` benenne nur eine Instanz des `ID` da `companyIDs` und `orderIDs` müssen nicht die gleichen Eigenschaften.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Anonyme Typen](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)