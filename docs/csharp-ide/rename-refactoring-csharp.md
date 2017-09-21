---
title: "Umgestaltung durch Umbenennen (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.rename"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Umgestaltung [C#], durch Umbenennen"
  - "Umgestaltung durch Umbenennen [C#]"
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
caps.handback.revision: 45
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Umgestaltung durch Umbenennen (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Umbenennen** ist ein Umgestaltungsfeature in der IDE \(integrierte Entwicklungsumgebung\) von Visual Studio, mit dem Sie auf einfache Weise Bezeichner für Codesymbole wie Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen umbenennen können.  **Umbenennen** kann verwendet werden, um die Namen in Kommentaren und Zeichenfolgen sowie Deklarationen und Aufrufe eines Bezeichners zu ändern.  
  
> [!NOTE]
>  Wenn Sie die die Quellcodeverwaltung von Visual Studio verwenden, rufen Sie die neueste Version der Quellen ab, bevor Sie die Umgestaltung mit Umbenennen ausführen.  
  
 Die Umgestaltung mit Umbenennen ist in den folgenden Visual Studio\-Features verfügbar:  
  
|Funktion|Verhalten der Umgestaltung in der IDE|  
|--------------|-------------------------------------------|  
|Code\-Editor|Im Code\-Editor ist die Umgestaltung mit Umbenennen verfügbar, wenn Sie den Cursor auf bestimmten Codesymboltypen positionieren.  Wenn der Cursor an dieser Position befindet, können Sie den Befehl **Umbenennen** aufrufen, indem Sie die Tastenkombination eingeben \(STRG\+R, STRG\+ R\) oder durch Auswählen des Befehls **Umbenennen** von einem Smarttag, im Kontextmenü oder aus dem Menü **Umgestalten**.|  
|Klassenansicht|Wenn Sie einen Bezeichner in der Klassenansicht auswählen, ist die Umgestaltung mit Umbenennen im Kontextmenü und im Menü **Umgestalten** verfügbar.|  
|Objektkatalog|Wenn Sie einen Bezeichner im Objektkatalog auswählen, ist die Umgestaltung mit Umbenennen nur im Menü **Umgestalten** verfügbar.|  
|Eigenschaftenraster des Windows Forms\-Designers|Wenn Sie den Namen eines Steuerelements im **Eigenschaftenraster** des Windows Forms\-Designers ändern, wird ein Umbenennungsvorgang für dieses Steuerelement gestartet.  Das Dialogfeld **Umbenennen** wird nicht angezeigt.|  
|Projektmappen\-Explorer|Im **Projektmappen\-Explorer** ist der Befehl **Umbenennen** im Kontextmenü verfügbar.  Wenn die ausgewählte Quelldatei eine Klasse enthält, deren Klassenname dem Dateinamen entspricht, können Sie mit diesem Befehl die Quelldatei umbenennen und gleichzeitig die Umgestaltung mit Umbenennen ausführen.<br /><br /> Wenn Sie beispielsweise eine Windows\-Standardanwendung erstellen und dann Form1.cs in TestForm.cs umbenennen, wird der Quelldateiname Form1.cs in TestForm.cs geändert, und die Klasse Form1 sowie alle Verweise auf diese Klasse werden in TestForm umbenannt. **Note:**  Durch den Befehl **Rückgängig** \(STRG\+Z\) wird die Umgestaltung mit Umbenennen nur im Code rückgängig gemacht. Der Dateiname wird nicht in den ursprünglichen Namen zurückgeändert. <br /><br /> Wenn die ausgewählte Quelldatei keine Klasse enthält, deren Name mit dem Dateinamen übereinstimmt, wird durch den Befehl **Umbenennen** im **Projektmappen\-Explorer** nur die Quelldatei umbenannt und keine Umgestaltung mit Umbenennen ausgeführt.|  
  
## Umbenennungsvorgänge  
 Wenn Sie **Umbenennen** ausführen, führt das Umgestaltungsmodul für die einzelnen Codesymbole spezifische Umbenennungsvorgänge aus, wie in der folgenden Tabelle beschrieben.  
  
|Codesymbol|Umbenennungsvorgang|  
|----------------|-------------------------|  
|Feld|Ändert die Deklaration und alle Verwendungen des Felds in den neuen Namen.|  
|Lokale Variable|Ändert die Deklaration und Vorkommen der Variablen in den neuen Namen.|  
|Methode|Ändert den Namen der Methode und alle Verweise auf diese Methode in den neuen Namen. **Note:**  Wenn Sie eine vorhandene Methode umbenenne, wird die Umbenennung auf alle Instanzen der Methode angewendet, die sich im Gültigkeitsbereich befinden, und zwar unabhängig davon, ob eine Erweiterungsmethode als statische Methode oder Instanzmethode verwendet wird.  Weitere Informationen finden Sie unter [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Namespace|Ändert den Namen des Namespaces in der Deklaration, allen `using`\-Anweisungen und vollqualifizierten Namen in den neuen Namen. **Note:**  Beim Umbenennen eines Namespaces aktualisiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auch die **Standardnamespace**\-Eigenschaft auf der Seite **Anwendung** des **Projekt\-Designers**.  Diese Eigenschaft kann durch Auswahl von **Rückgängig** im Menü **Bearbeiten** nicht zurückgesetzt werden.  Um den Wert der **Standardnamespace**\-Eigenschaft zurückzusetzen, müssen Sie die Eigenschaft im **Projekt\-Designer** ändern.  Weitere Informationen finden Sie unter [Seite 'Anwendung'](../ide/reference/application-page-project-designer-csharp.md).|  
|Eigenschaft|Ändert die Deklaration und alle Verwendungen der Eigenschaft in den neuen Namen.|  
|Text \[Type\]|Ändert alle Deklarationen und Vorkommen des Typs, einschließlich Konstruktoren und Destruktoren, in den neuen Namen.  Bei partiellen Typen wirkt sich der Umbenennungsvorgang auf alle Teile aus.|  
  
#### So benennen Sie einen Bezeichner um  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `RenameIdentifier`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```c#  
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
  
2.  Positionieren Sie den Cursor entweder in der Methodendeklaration oder im Methodenaufruf auf `MethodB`.  
  
3.  Klicken Sie im Menü **Umgestalten** auf **Umbenennen**.  Das Dialogfeld **Umbenennen** wird angezeigt.  
  
     Sie können auch mit der rechten Maustaste auf den Cursor klicken, im Kontextmenü auf **Umgestalten** zeigen und dann auf **Umbenennen** klicken, um das Dialogfeld **Umbenennen** anzuzeigen.  
  
4.  Geben Sie im Feld **Neuer Name** den Eintrag `MethodC` ein.  
  
5.  Aktivieren Sie das Kontrollkästchen **In Kommentaren suchen**.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Klicken Sie im Dialogfeld **Vorschau der Änderungen** auf **Übernehmen**.  
  
#### So benennen Sie einen Bezeichner mithilfe von Smarttags um  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `RenameIdentifier`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```c#  
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
  
2.  Überschreiben Sie den Methodenbezeichner in der Deklaration für `MethodB`, oder löschen Sie ihn mit der RÜCKTASTE.  Eine Smarttag\-Eingabeaufforderung wird unterhalb dieses Bezeichners angezeigt.  
  
    > [!NOTE]
    >  Die Umgestaltung mit Umbenennen kann an der Deklaration eines Bezeichners nur mithilfe von Smarttags aufgerufen werden.  
  
3.  Drücken Sie die Tastenkombination UMSCHALT\+ALT\+F10 und anschließend die NACH\-UNTEN\-TASTE, um das Smarttag\-Menü anzuzeigen.  
  
     \- oder \-  
  
     Verschieben Sie den Mauszeiger über die Smarttag\-Eingabeaufforderung, um das Smarttag anzuzeigen.  Verschieben Sie den Mauszeiger dann über das Smarttag, und klicken Sie auf den nach unten weisenden Pfeil, um das Smarttag\-Menü anzuzeigen.  
  
4.  Wählen Sie das Menüelement **'**\<Bezeichner1\>**' in '**\<Bezeichner2\>**' umbenennen** aus, um die Umgestaltung mit Umbenennen ohne Vorschau der Änderungen für den Code aufzurufen.  Alle Verweise auf \<Bezeichner1\> werden automatisch auf \<Bezeichner2\> aktualisiert.  
  
     \- oder \-  
  
     Wählen Sie das Menüelement **Umbenennen mit Vorschau** aus, um die Umgestaltung mit Umbenennen aufzurufen und gleichzeitig eine Vorschau der Änderungen am Code anzuzeigen.  Das Dialogfeld **Vorschau der Änderungen** wird angezeigt.  
  
## Hinweise  
  
## Umbenennen implementiert oder überschriebene Member  
 Wenn Sie einen Member **umbenennen**, der Member in anderen Typen implementiert\/überschreibt bzw. von Membern in anderen Typen implementiert\/überschrieben wird, zeigt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Dialogfeld an, in dem Sie darauf hingewiesen werden, dass der Umbenennungsvorgang zu kaskadierenden Aktualisierungen führt.  Wenn Sie auf **Weiter** klicken, führt das Umgestaltungsmodul eine rekursive Suche und Umbenennung aller Member in Basistypen und abgeleiteten Typen aus, die in einer Implementierungs\-\/Überschreibungsbeziehung zu dem umbenannten Member stehen.  
  
 Das folgende Codebeispiel enthält Member mit Implementierungs\-\/Überschreibungsbeziehungen.  
  
 [!code-cs[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 Im vorherigen Beispiel wird durch das Umbenennen von `C.Method()` auch `Ibase.Method()` umbenannt, da `Ibase.Method()` von `C.Method()` implementiert wird.  In einer rekursiven Suche erkennt das Umgestaltungsmodul daraufhin, dass `Ibase.Method()` von `Derived.Method()` implementiert wird und benennt `Derived.Method()` um.  `Base.Method()` benennt das Umgestaltungsmodul hingegen nicht um, da `Base.Method()` von `Derived.Method()` nicht überschrieben wird.  Sofern im Dialogfeld **Umbenennen** nicht die Option **Überladungen umbenennen** aktiviert ist, stoppt das Umgestaltungsmodul an dieser Stelle.  
  
 Wenn **Überladungen umbenennen** aktiviert ist, benennt das Umgestaltungsmodul `Derived.Method(int i)` um, weil es `Derived.Method()` überlädt, `Base.Method(int i)`, weil es von `Derived.Method(int i)` überschrieben wird und `Base.Method()`, weil es eine Überladung von `Base.Method(int i)` ist.  
  
> [!NOTE]
>  Wenn Sie einen Member umbenennen, der in einer referenzierten Assembly definiert wurde, werden Sie in einem Dialogfeld darauf hingewiesen, das die Umbenennung zu Buildfehlern führt.  
  
## Umbenennen von Eigenschaften anonymer Typen  
 Wenn Sie eine Eigenschaft anonymer Typen umbenennen, wird der Umbenennungsvorgang auch für Eigenschaften in anderen anonymen Typen, die über die gleichen Eigenschaften verfügen, durchgeführt.  Dieses Verhalten wird im folgenden Beispiel veranschaulicht:  
  
```c#  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Im vorhergehenden Code führt das Umbenennen der `ID` zur Änderung der `ID` in beiden Anweisungen, da sie über den gleichen zugrunde liegenden anonymen Typ verfügen.  
  
```c#  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Im vorhergehenden Code führt das Umbenennen von `ID` nur zum Umbenennen einer Instanz von `ID`, da `companyIDs` und `orderIDs` nicht über die gleichen Eigenschaften verfügen.  
  
## Siehe auch  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Anonyme Typen](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)