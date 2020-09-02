---
title: Refactoring umbenennen (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667477"
---
# <a name="rename-refactoring-c"></a>Umgestaltung durch Umbenennen (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Rename** ist eine Refactoringfunktion in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio, die eine einfache Möglichkeit zum Umbenennen von bezeichmern für Code Symbole wie Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen bietet. **Umbenennen** kann verwendet werden, um die Namen in Kommentaren und Zeichen folgen zu ändern und die Deklarationen und Aufrufe eines Bezeichners zu ändern.

> [!NOTE]
> Wenn Sie die Quell Code Verwaltung für Visual Studio verwenden, sollten Sie die neueste Version der Quellen erhalten, bevor Sie versuchen, Umbenennungs Umgestaltung auszuführen.

 Refactoring umbenennen ist in den folgenden Visual Studio-Features verfügbar:

|Funktion|Verhalten der Umgestaltung in der IDE|
|-------------|----------------------------------------|
|Code-Editor|Im Code-Editor ist Refactoring Umbenennen verfügbar, wenn Sie den Cursor auf bestimmten Typen von Code Symbolen positionieren. Wenn sich der Cursor an dieser Position befindet, können Sie den Befehl **Umbenennen** aufrufen, indem Sie die Tastenkombination (Strg + r, Strg + r) eingeben, oder indem Sie den Befehl **Umbenennen** in einem Smarttag, einem Kontextmenü oder dem Menü **umgestalten** auswählen.|
|Klassenansicht|Wenn Sie in Klassenansicht einen Bezeichner auswählen, ist im Kontextmenü und **Umgestaltungs** Menü die Option Umgestaltung umbenennen verfügbar.|
|Objektkatalog|Wenn Sie einen Bezeichner in Objektkatalog auswählen, ist Refactoring umbenennen nur über das Menü **umgestalten** verfügbar.|
|Eigenschaften Raster der Windows Forms-Designer|Im **Eigenschaften Raster** des Windows Forms-Designer wird durch das Ändern des Namens eines Steuer Elements ein Umbenennungs Vorgang für dieses Steuerelement initiiert. Das Dialogfeld **Umbenennen** wird nicht angezeigt.|
|Projektmappen-Explorer|In **Projektmappen-Explorer**ist ein **Rename** -Befehl im Kontextmenü verfügbar. Wenn die ausgewählte Quelldatei eine Klasse enthält, deren Klassenname mit dem Dateinamen identisch ist, können Sie diesen Befehl verwenden, um die Quelldatei gleichzeitig umzubenennen und Umbenennungs Umgestaltung auszuführen.<br /><br /> Wenn Sie z. b. eine standardmäßige Windows-basierte Anwendung erstellen und dann Form1.cs in TestForm.cs umbenennen, ändert sich der Quell Dateiname Form1.cs in TestForm.cs, und die Klasse Form1 und alle Verweise auf diese Klasse werden in TestForm umbenannt. **Hinweis:**  Der Befehl " **Rückgängig** " (STRG + Z) macht nur Umbenennungs Umgestaltung im Code rückgängig, und der Dateiname wird nicht wieder in den ursprünglichen Namen geändert. <br /><br /> Wenn die ausgewählte Quelldatei keine Klasse enthält, deren Name mit dem Dateinamen identisch ist, benennt der **Rename** -Befehl in **Projektmappen-Explorer** nur die Quelldatei um und führt keine Umgestaltung zum Umbenennen aus.|

## <a name="rename-operations"></a>Umbenennungs Vorgänge
 Wenn Sie **Rename**ausführen, führt die Refactoring-Engine einen Umbenennungs Vorgang speziell für jedes Code Symbol aus, wie in der folgenden Tabelle beschrieben.

|Code Symbol|Umbenennungs Vorgang|
|-----------------|----------------------|
|Feld|Ändert die Deklaration und die Verwendungen des Felds in den neuen Namen.|
|Lokale Variable|Ändert die Deklaration und die Verwendungen der Variablen in den neuen Namen.|
|Methode|Ändert den Namen der Methode und alle Verweise auf diese Methode in den neuen Namen. **Hinweis:**  Wenn Sie eine Erweiterungsmethode umbenennen, wird der Umbenennungs Vorgang an alle Instanzen der Methode weitergegeben, die sich im Gültigkeitsbereich befinden, unabhängig davon, ob die Erweiterungsmethode als statische Methode oder Instanzmethode verwendet wird. Weitere Informationen finden Sie unter [Erweiterungsmethoden](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Namespace|Ändert den Namen des Namespace in der Deklaration, allen `using` Anweisungen und voll qualifizierten Namen in den neuen Namen. **Hinweis:**  Wenn Sie einen Namespace umbenennen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktualisiert auch die Eigenschaft **Standard Namespace** auf der Seite **Anwendung** des **Projekt-Designers**. Diese Eigenschaft kann nicht zurückgesetzt werden, indem Sie im Menü **Bearbeiten** die Option **Rückgängig** auswählen. Zum Zurücksetzen des **Standard Namespace** -Eigenschafts Werts müssen Sie die-Eigenschaft im **Projekt-Designer**ändern. Weitere Informationen finden Sie unter [Seite "Anwendung](../ide/reference/application-page-project-designer-csharp.md)".|
|Eigenschaft|Ändert die Deklaration und die Verwendungen der Eigenschaft in den neuen Namen.|
|type|Ändert alle Deklarationen und alle Verwendungen des Typs in den neuen Namen, einschließlich Konstruktoren und Dekonstruktoren. Bei partiellen Typen wird der Umbenennungs Vorgang an alle Teile weitergegeben.|

#### <a name="to-rename-an-identifier"></a>So benennen Sie einen Bezeichner um

1. Erstellen Sie eine Konsolenanwendung mit dem Namen `RenameIdentifier`, und ersetzen Sie `Program` durch den folgenden Beispielcode.

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

2. Platzieren Sie den Cursor `MethodB` entweder in der Methoden Deklaration oder im Methoden Aufruf.

3. Wählen Sie im Menü **umgestalten** die Option **Umbenennen**aus. Das Dialogfeld **Umbenennen** wird angezeigt.

     Sie können auch mit der rechten Maustaste auf den Cursor klicken, im Kontextmenü auf **umgestalten** zeigen und dann auf **Umbenennen** klicken, um das Dialogfeld **Umbenennen** anzuzeigen.

4. Geben Sie im Feld **neuer Name den Namen** ein `MethodC` .

5. Aktivieren Sie das Kontrollkästchen **in Kommentaren suchen** .

6. Klicken Sie auf **OK**.

7. Klicken Sie im Dialogfeld **Vorschau** der Änderungen **auf über**nehmen.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>So benennen Sie einen Bezeichner mit Smarttags um

1. Erstellen Sie eine Konsolenanwendung mit dem Namen `RenameIdentifier`, und ersetzen Sie `Program` durch den folgenden Beispielcode.

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

2. Geben Sie in der Deklaration für `MethodB` den Methoden Bezeichner oder Rücklauf ein. Unterhalb dieses Bezeichners wird eine Smarttag-Eingabeaufforderung angezeigt.

    > [!NOTE]
    > Sie können die Umbenennungs Umgestaltung nur mit Smarttags in der Deklaration eines Bezeichners aufrufen.

3. Geben Sie die Tastenkombination UMSCHALT + ALT + F10 ein, und klicken Sie dann auf den Pfeil nach unten, um das Smarttag-Menü anzuzeigen.

     - oder -

     Bewegen Sie den Mauszeiger über die Smarttag-Eingabeaufforderung, um das Smarttag anzuzeigen. Bewegen Sie dann den Mauszeiger über das Smarttag, und klicken Sie auf den Pfeil nach unten, um das Smarttag-Menü anzuzeigen.

4. Wählen Sie das Menü Element **" \<identifer1> " \<identifier2> in "" Umbenennen** aus, um Umbenennungs Umgestaltung ohne Vorschau der Änderungen an Ihrem Code aufzurufen. Alle Verweise auf werden **\<identifer1>** automatisch auf aktualisiert **\<identifier2>** .

     - oder -

     Wählen Sie das Menü Element **Umbenennen mit Vorschau** aus, um Umbenennungs Umgestaltung mit einer Vorschau der Änderungen an Ihrem Code aufzurufen. Das Dialogfeld **Vorschau der Änderungen** wird angezeigt.

## <a name="remarks"></a>Bemerkungen

## <a name="renaming-implemented-or-overridden-members"></a>Umbenennen implementierter oder überschriebener Member
 Wenn Sie einen Member **Umbenennen** , der entweder implementiert bzw. außer Kraft gesetzt oder von Membern in anderen Typen implementiert bzw. überschrieben wird, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zeigt ein Dialogfeld an, das besagt, dass der Umbenennungs Vorgang zu kaskadierenden Updates führt. Wenn Sie auf " **weiter**" klicken, sucht die Refactoring-Engine rekursiv alle Elemente in Basis Typen und abgeleiteten Typen, die über die Beziehung "implementiert"/"Overrides" mit dem umbenannten Member verfügen.

 Das folgende Codebeispiel enthält Elemente mit implementierten/über schreibungen-Beziehungen.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 Im vorherigen Beispiel wird durch das Umbenennen `C.Method()` ebenfalls umbenannt, `Ibase.Method()` da `C.Method()` implementiert `Ibase.Method()` . Im nächsten Schritt wird die umgestalten Engine rekursiv sehen, dass `Ibase.Method()` von implementiert wird `Derived.Method()` und umbenannt wird `Derived.Method()` . Die umgestalten Engine wird nicht umbenannt `Base.Method()` , da von `Derived.Method()` nicht überschrieben wird `Base.Method()` . Die Refactoring-Engine wird hier angehalten, es sei denn, Sie haben **über Ladungen umbenennen** im Dialogfeld **Umbenennen** aktiviert.

 Wenn **Überladungen umbenennen** aktiviert ist, wird die Umgestaltungs-Engine umbenannt `Derived.Method(int i)` , da `Derived.Method()` Sie `Base.Method(int i)` überladen wird, da Sie von überschrieben wird, `Derived.Method(int i)` und da es sich um eine Überladung `Base.Method()` von handelt `Base.Method(int i)` .

> [!NOTE]
> Wenn Sie einen Member umbenennen, der in einer referenzierten Assembly definiert wurde, wird in einem Dialogfeld erläutert, dass das Umbenennen zu Buildfehlern führt.

## <a name="renaming-properties-of-anonymous-types"></a>Umbenennen von Eigenschaften anonymer Typen
 Wenn Sie eine Eigenschaft in anonymen Typen umbenennen, wird der Umbenennungs Vorgang an Eigenschaften in anderen anonymen Typen weitergegeben, die über die gleichen Eigenschaften verfügen. In den folgenden Beispielen wird dieses Verhalten veranschaulicht.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 Im vorangehenden Code wird die Umbenennung `ID` `ID` in beiden Anweisungen geändert, da Sie denselben zugrunde liegenden anonymen Typ aufweisen.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 Im vorangehenden Code `ID` wird durch das Umbenennen nur eine Instanz von umbenannt, `ID` da `companyIDs` und `orderIDs` nicht über die gleichen Eigenschaften verfügen.

## <a name="see-also"></a>Weitere Informationen
 Anonyme [Refactoring-Typen (c#)](../csharp-ide/refactoring-csharp.md) [Anonymous Types](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)