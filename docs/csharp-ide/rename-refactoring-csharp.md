---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: Benennen Sie die Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eba5a9f55e5d3d08eee48dc083a7e2f848118162
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="rename-refactoring-c"></a>Umgestaltung durch Umbenennen (C#)
**Benennen Sie** ist eine Umgestaltung Funktion in der Visual Studio integrierten Entwicklungsumgebung (IDE), die eine einfache Möglichkeit zum Umbenennen von Bezeichnern für Codesymbole wie Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen bereitstellt. **Benennen Sie** kann verwendet werden, so ändern Sie die Namen in Kommentaren und Zeichenfolgen und Deklarationen und Aufrufe eines Bezeichners zu ändern.  
  
> [!NOTE]
>  Bei Verwendung der Quellcodeverwaltung für Visual Studio werden abrufen Sie die neueste Version von Quellen, bevor Sie versuchen, Umgestaltung mit Umbenennung auszuführen.  
  
 Umgestaltung mit Umbenennen sind über die folgenden Visual Studio-Funktionen verfügbar:  
  
|Funktion|Verhalten der Umgestaltung in der IDE|  
|-------------|----------------------------------------|  
|Code-Editor|Im Code-Editor ist die Umgestaltung mit Umbenennen verfügbar, wenn Sie den Cursor auf bestimmte Arten von Codesymbole positionieren. Wenn der Cursor an dieser Position befindet, können Sie Aufrufen der **umbenennen** Befehl durch Eingeben der Tastenkombination (STRG + R, STRG + R) oder durch Auswählen der **umbenennen** Befehl Schnellaktionen, die Sie im Kontextmenü oder die **Umgestalten** Menü.|  
|Klassenansicht|Wenn Sie einen Bezeichner in der Klassenansicht auswählen, Umgestaltung mit Umbenennen steht über das Kontextmenü und **Umgestalten** Menü.|  
|Objektkatalog|Bei der Auswahl eines Bezeichners im Objektkatalog Umgestaltung mit Umbenennen steht nur aus den **Umgestalten** Menü.|  
|Eigenschaftenraster des Windows Forms-Designer|In der **Eigenschaftenraster** von Windows Forms-Designer ändern des Namens eines Steuerelements ein Umbenennungsvorgang für dieses Steuerelement initiiert wird. Die **umbenennen** Dialogfeld nicht angezeigt wird.|  
|Projektmappen-Explorer|In **Projektmappen-Explorer**, **umbenennen** Befehl im Kontextmenü verfügbar ist. Wenn die ausgewählte Quelldatei eine Klasse enthält, deren Klassenname mit dem Dateinamen identisch ist, können Sie mit diesem Befehl verwenden, gleichzeitig die Quelldatei umbenannt und Umgestaltung mit Umbenennen.<br /><br /> Z. B., wenn Sie eine standardmäßige Windows-basierte Anwendung erstellen und Sie dann "Form1.cs" in TestForm.cs benennen, der Name der Quelldatei "Form1.cs" ändert sich TestForm.cs und die Klasse Form1 und alle Verweise auf, dass die Klasse zum TestForm umbenannt wird. **Hinweis:** der **Rückgängig** Befehl (STRG + Z) nur rückgängig machen, Umgestaltung mit Umbenennen im Code und wird nicht ändern, die der Dateinamen zurück, in den ursprünglichen Namen. <br /><br /> Wenn die ausgewählte Quelldatei keine Klasse enthalten, deren Name der Name der Datei entspricht, die **umbenennen** -Befehl in **Projektmappen-Explorer** werden nur die Quelldatei umbenannt und Umbenennen wird nicht ausgeführt Umgestaltung.|  
  
## <a name="rename-operations"></a>Umbenennen von Vorgängen  
 Beim Ausführen **umbenennen**, führt das refactoring Modul spezifische Umbenennungsvorgänge für jedes Symbol Code aus, wie in der folgenden Tabelle beschrieben.  
  
|Code-Symbol|Umbenennen (Vorgang)|  
|-----------------|----------------------|  
|Feld|Ändert die Deklaration und Verwendung des Felds in den neuen Namen an.|  
|lokale variable|Ändert die Deklaration und Verwendung der Variablen in den neuen Namen an.|  
|Methode|Ändert den Namen der Methode und alle Verweise auf diese Methode in den neuen Namen an. **Hinweis:** beim Umbenennen einer Erweiterungsmethode gibt den Umbenennungsvorgang für alle Instanzen der Methode, die im Gültigkeitsbereich befindet, unabhängig davon, ob die Erweiterungsmethode als eine statische Methode oder Instanzmethode verwendet wird. Weitere Informationen finden Sie unter [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Namespace|Der Name des Namespaces in den neuen Namen in der Deklaration ändert alle `using` Anweisungen und den vollqualifizierten Namen. **Hinweis:** beim Umbenennen eines Namespaces [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden auch aktualisiert, die **Default Namespace** Eigenschaft auf die **Anwendung** auf der Seite der **Projekt-Designer**. Diese Eigenschaft kann nicht zurückgesetzt werden, indem Sie auswählen **Rückgängig** aus der **bearbeiten** Menü. Zurücksetzen der **Default Namespace** Eigenschaftswert, müssen Sie die Eigenschaft im Ändern der **Projekt-Designer**. Weitere Informationen finden Sie unter [Seite "Anwendung"](../ide/reference/application-page-project-designer-csharp.md).|  
|Eigenschaft|Ändert die Deklaration und Verwendung der Eigenschaft in den neuen Namen an.|  
|Typ|Ändert alle Deklarationen und alle Verwendungen des Typs in den neuen Namen ein, einschließlich Konstruktoren und Destruktoren. Für partielle Typen wird der Umbenennungsvorgang für alle Teile.|  
  
#### <a name="to-rename-an-identifier"></a>Umbenennen ein Bezeichners  
  
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
  
2.  Platzieren Sie den Cursor auf `MethodB`, entweder in der Deklaration der Methode oder dem Aufruf der Methode.  
  
3.  Aus der **Umgestalten** klicken Sie im Menü **umbenennen**. Die **umbenennen** Dialogfeld wird angezeigt.  
  
     Sie können auch mit der rechten Maustaste des Mauszeiger, zeigen Sie auf **Umgestalten** auf das Kontextmenü, und klicken Sie dann auf **umbenennen** zum Anzeigen der **umbenennen** (Dialogfeld).  
  
4.  In der **neuen Namen** Feld `MethodC`.  
  
5.  Wählen Sie die **Suche in den Kommentaren** Kontrollkästchen.  
  
6.  Klicken Sie auf **OK**.  
  
7.  In der **Vorschau der Änderungen** (Dialogfeld), klicken Sie auf **übernehmen**.  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>Einen Bezeichner, die mithilfe von Schnellaktionen umbenennen  
  
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
  
2.  In der Deklaration für `MethodB`, oder geben Sie die RÜCKTASTE über den Methodenbezeichner. Am Rand wird eine Glühbirne Schnellaktionen angezeigt.  
  
    > [!NOTE]
    >  Sie können nur aufrufen, Umgestaltung mit Umbenennung mithilfe von Schnellaktionen bei der Deklaration eines Bezeichners.  
  
3.  Geben Sie die Tastenkombination **Umschalt + Alt + F10** schnelle Aktionsmenü angezeigt.  
  
     - oder -   
  
     Klicken Sie auf das schwarze Dreieck neben die Glühbirne, um das Menü Schnellaktionen anzuzeigen.  
  
4.  Wählen Sie die **umbenennen "\<identifer1 >", "\<Bezeichner2 >"** Menüelement aufzurufenden Umgestaltung mit Umbenennen. Alle Verweise auf  **\<identifer1 >** werden automatisch aktualisiert werden, um  **\<Bezeichner2 >**.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="renaming-implemented-or-overridden-members"></a>Umbenennen von implementiert oder überschriebene Member  
 Wenn Sie **umbenennen** ein Element, das implementiert/überschreibt bzw. implementiert/Überschreiben von Membern in andere Typen wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zeigt ein Dialogfeld mit dem Hinweis angezeigt, der Umbenennungsvorgang führt dazu, dass updateweitergaben an. Wenn Sie auf **Fortfahren**, die Umgestaltung Modul rekursiv findet und benennt alle Member in Basis und abgeleiteten Typen, implementiert/überschreibt Beziehungen mit dem Element, das umbenannt wird.  
  
 Das folgende Codebeispiel enthält Elemente mit implementiert/Außerkraftsetzungen Beziehungen.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 Im vorherigen Beispiel umbenennen `C.Method()` auch benennt `Ibase.Method()` da `C.Method()` implementiert `Ibase.Method()`. Als Nächstes die Umgestaltung Modul rekursiv erkennt, dass `Ibase.Method()` wird dadurch implementiert, `Derived.Method()` und benennt `Derived.Method()`. Das Umgestaltungsmodul, nicht umbenannt `Base.Method()`, da `Derived.Method()` überschreibt nicht `Base.Method()`. Die Umgestaltung des Datenbankmoduls wird hier beendet, es sei denn, Sie haben **umbenennen Überladungen** eingecheckt der **umbenennen** (Dialogfeld).  
  
 Wenn **umbenennen Überladungen** aktiviert ist, wird das Umgestaltungsmodul für die benennt `Derived.Method(int i)` , da sie überlädt `Derived.Method()`, `Base.Method(int i)` , da er von überschrieben wird `Derived.Method(int i)`, und `Base.Method()` , da es sich um eine Überladung ist `Base.Method(int i)`.  
  
> [!NOTE]
>  Wenn Sie ein Element, die in einer referenzierten Assembly definiert wurde umbenennen, wird ein Dialogfeld an, dass es sich bei Umbenennen Buildfehler verursacht wird.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Umbenennen von Eigenschaften von anonymen Typen  
 Wenn Sie eine Eigenschaft in anonymen Typen umbenennen, wird der Umbenennungsvorgang Eigenschaften im anderen anonymen Typen weitergegeben werden, die die gleichen Eigenschaften verfügen. Die folgenden Beispiele veranschaulichen dieses Verhalten.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Im vorangehenden Code umbenennen `ID` ändert sich `ID` in beiden Anweisungen, da sie die gleichen zugrunde liegenden anonymen Typ aufweisen.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Im vorangehenden Code umbenennen `ID` wird nur eine Instanz des umbenennen `ID` da `companyIDs` und `orderIDs` müssen nicht die gleichen Eigenschaften.  
  
## <a name="see-also"></a>Siehe auch  
 [Umgestaltung (c#)](refactoring-csharp.md)   
 [Anonyme Typen](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)