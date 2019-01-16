---
title: Erstellen benutzerdefinierter Ansichten von systemeigenen Objekten
description: Verwenden Sie das Natvis-Framework anpassen, dass Visual Studio systemeigene Typen im Debugger angezeigt.
ms.date: 10/31/2018
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d91a62971db47b78b974cc2dede77d0a47b5c851
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821191"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>Erstellen benutzerdefinierter Ansichten nativer Objekte im Debugger

Visual Studio *Natvis* Framework passt die Möglichkeit, native Typen in Variablenfenstern des Debuggers, z. B. werden, die **"lokal"** und **Watch** Windows und **DataTips**. Natvis-Visualisierungen können die Typen zu, die Sie während des Debuggens besser sichtbar zu erstellen. 

Natvis ersetzt die *autoexp.dat* Datei in früheren Versionen von Visual Studio mit XML-Syntax, bessere Diagnose, versionsverwaltung und mehrere Dateitypen unterstützen.  

Natvis funktioniert nicht für:

- C++-Windows-Desktop-Projekte mit **Debuggertyp** festgelegt **gemischt** unter **Konfigurationseigenschaften** > **Debuggen**. 
- [Debuggen im gemischten Modus](how-to-debug-in-mixed-mode.md) für Windows desktop-apps im verwalteten Kompatibilitätsmodus (**Tools** > **Optionen** > **Debuggen**  >  **Allgemeine** > **verwalteten Kompatibilitätsmodus verwenden**).

## <a name="BKMK_Why_create_visualizations_"></a>Natvis-Visualisierungen

Sie verwenden das Natvis-Framework zum Erstellen von visualisierungsregeln für Typen, die Sie erstellen, damit Entwickler während des Debuggens leichter angezeigt werden können.  

Die folgende Abbildung zeigt z. B. eine Variable vom Typ [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) in einem Debuggerfenster ohne angewendete benutzerdefinierten Visualisierungen.  

![TextBox-standardvisualisierung](../debugger/media/dbg_natvis_textbox_default.png "TextBox-standardvisualisierung")  

Die hervorgehobene Zeile zeigt die `Text` -Eigenschaft der `TextBox` -Klasse. Die komplexe Klassenhierarchie erschwert diese Eigenschaft zu suchen. Der Debugger weiß nicht, wie benutzerdefinierte Zeichenfolgentyp, zu interpretieren, damit Sie im Textfeld enthaltene Zeichenfolge nicht sehen können.  

Die gleiche `TextBox` im Variablenfenster viel einfacher aussieht, wenn die benutzerdefinierte Schnellansicht Natvis-Regeln angewendet werden. Die wichtigen Member der Klasse zusammen angezeigt werden, und der Debugger zeigt den zugrunde liegenden Zeichenfolgenwert des benutzerdefinierten Zeichenfolgentyps.  

![TextBox-Daten mit Schnellansicht](../debugger/media/dbg_natvis_textbox_visualizer.png "TextBox-Daten mit Schnellansicht")  

##  <a name="BKMK_Using_Natvis_files"></a>Verwenden von natvis-Dateien in C++-Projekten  

Natvis verwendet *natvis* Dateien visualisierungsregeln angegeben. Ein *natvis* Datei ist eine XML-Datei mit einem *natvis* Erweiterung. Das Natvis-Schema wird definiert, *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.  

Die grundlegende Struktur einer *natvis* Datei enthält eine oder mehrere `Type` Elementen visualisierungseinträgen darstellen. Der vollqualifizierte Name der einzelnen `Type` Element wird angegeben, dessen `Name` Attribut.  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  

  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  

Visual Studio sind einige *natvis* Dateien in die *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* Ordner. Diese Dateien haben visualisierungsregeln für viele allgemeine Typen und können als Beispiele dienen, für das Schreiben von Visualisierungen für neue Typen.  

### <a name="add-a-natvis-file-to-a-c-project"></a>Eine natvis-Datei zu einem C++-Projekt hinzufügen  

Sie können Hinzufügen einer *natvis* Datei zu einem C++-Projekt.  

**Zum Hinzufügen einer neuen *natvis* Datei:**

1. Wählen Sie den C++-Projektknoten im **Projektmappen-Explorer**, und wählen Sie **Projekt** > **neues Element hinzufügen**, oder mit der rechten Maustaste in des Projekts, und wählen Sie **hinzufügen**   >  **Neues Element**.
   
1. In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Visual C++** > **Hilfsprogramm** > **Debugger-visualisierungsdatei (.natvis)**. 
   
1. Nennen Sie die Datei, und wählen **hinzufügen**.
   
   Die neue Datei hinzugefügt wird **Projektmappen-Explorer**, und klicken Sie im Dokument Visual Studio geöffnet. 

Visual Studio-Debugger lädt *natvis* Dateien in C++-Projekte automatisch und in der Standardeinstellung enthält auch in der *PDB* -Datei, wenn das Projekt erstellt wird. Wenn Sie die erstellte app Debuggen, lädt der Debugger die *natvis* -Datei aus der *PDB* Datei, selbst wenn Sie das Projekt geöffnet haben. Wenn Sie nicht möchten die *natvis* enthaltene Datei die *PDB*, können Sie es von den integrierten ausschließen *PDB* Datei.

**Ausschließen einer *natvis* -Datei aus einer *PDB*:**

1. Wählen Sie die *natvis* Datei **Projektmappen-Explorer**, und wählen Sie die **Eigenschaften** Symbol, oder mit der rechten Maustaste in der das, und wählen **Eigenschaften**.
   
1. Löschen Sie den Pfeil nach unten neben **vom Build ausgeschlossen** , und wählen Sie **Ja**, und wählen Sie dann **OK**.  

>[!NOTE]
>Verwenden Sie für das Debuggen ausführbarer Projekten Projektmappenelemente hinzufügen einer *natvis* Dateien, die nicht Bestandteil der *PDB*, da kein C++-Projekt verfügbar ist.  

>[!NOTE]
>Natvis-Regeln aus geladen eine *PDB* gelten nur für die Typen in den Modulen, die die *PDB* bezieht sich auf. Z. B. wenn *Datei "Module1.pdb"* verfügt über eine Natvis-Eintrag für einen Typ namens `Test`, gilt diese nur für die `Test` -Klasse im *"Module1.dll"*. Wenn Sie ein anderes Modul ebenfalls eine Klasse, die mit dem Namen definiert `Test`, *Datei "Module1.pdb"* Natvis-Eintrag gilt nicht für sie.  

### <a name="BKMK_natvis_location"></a> Natvis-Dateispeicherorte  

Sie können hinzufügen *natvis* zu Ihrem Benutzerverzeichnis oder einem Systemverzeichnis, Dateien, wenn Sie für mehrere Projekte gelten sollen.  

Die *natvis* -Dateien in der folgenden Reihenfolge ausgewertet werden:  

1. Alle *natvis* Dateien, die in eingebettet sind eine *PDB* Sie Debuggen, es sei denn, die das geladene Projekt eine Datei mit dem gleichen Namen vorhanden ist.  

1. Alle *natvis* Dateien, die in einem geladenen C++-Projekt oder Projektmappe auf oberster Ebene sind. Diese Gruppe enthält alle geladenen C++-Projekte, einschließlich Klassenbibliotheken, jedoch keine Projekte in anderen Sprachen. 

1.  Das benutzerspezifische Natvis-Verzeichnis (z. B. *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).  

1.  Das systemweite Natvis-Verzeichnis (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Dieses Verzeichnis darf nicht die *natvis* Dateien, die mit Visual Studio installiert werden. Wenn Sie über Administratorberechtigungen verfügen, können Sie Dateien in dieses Verzeichnis hinzufügen.  

## <a name="modify-natvis-files-while-debugging"></a>Ändern von natvis-Dateien während des Debuggens  

Sie können eine *natvis* Datei in der IDE beim Debuggen von eines Projekts. Öffnen Sie die Datei in der gleichen Instanz von Visual Studio mit Debuggen, ändern Sie und speichern Sie sie. Sobald die Datei gespeichert wird, die **sehen Sie sich** und **"lokal"** Windows aktualisiert werden, um die Änderung zu übernehmen. 

Sie können auch hinzufügen oder Löschen von *natvis* Dateien in einer Projektmappe, die Sie Debuggen, und Visual Studio hinzugefügt oder entfernt die relevanten Visualisierungen.  

Kann nicht aktualisiert werden *natvis* in eingebettete *PDB* Dateien während des Debuggens.  

Wenn Sie ändern die *natvis* Datei außerhalb von Visual Studio die Änderungen nicht automatisch wirksam. Um die Debugger-Fenster zu aktualisieren, können Sie erneut auswerten der **.natvisreload** -Befehl in der **Watch** Fenster. Und dann die Änderungen wirksam werden, ohne die Debugsitzung neu gestartet wird.  

Auch die **.natvisreload** Befehl aus, um ein upgrade der *natvis* Datei auf eine neuere Version. Z. B. die *natvis* Datei kann in die quellcodeverwaltung eingecheckt sein, und Sie kürzlich vorgenommene Änderungen auswählen, die ein Benutzer erstellt haben möchten. 

##  <a name="BKMK_Expressions_and_formatting"></a> Ausdrücke und Formatierung  
Natvis-Visualisierungen verwenden C++-Ausdrücke, um anzuzeigende Datenelementen anzugeben. Neben den Verbesserungen und Einschränkungen der C++-Ausdrücke im Debugger, sind die in beschriebenen [Kontextoperator (C++)](../debugger/context-operator-cpp.md), beachten Sie Folgendes:  

- Natvis-Ausdrücke werden im Kontext des Objekts ausgewertet, das in der Schnellansicht und nicht im aktuellen Stapelrahmen angezeigt wird. Z. B. `x` in einem Natvis-Ausdruck verweist auf das Feld **x** in das visualisierte Objekt, nicht um eine lokale Variable namens **x** in der aktuellen Funktion. Sie können keine lokale Variablen in Natvis-Ausdrücken zugreifen, obwohl Sie globale Variablen zugreifen können.  

- Natvis-Ausdrücken können keine funktionsauswertung oder Nebeneffekte auftreten. Funktionsaufrufe und Zuweisungsoperatoren werden ignoriert. Da [systeminterne Debuggerfunktionen](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) keine Nebeneffekte haben, können sie beliebig von jedem Natvis-Ausdruck aufgerufen werden, obwohl andere Funktionsaufrufe nicht zulässig sind.  

- Um zu steuern, wie ein Ausdruck angezeigt, können Sie jede der beschriebenen Formatbezeichner verwenden [Formatbezeichner in C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Formatbezeichner werden ignoriert, wenn der Eintrag, z. B. intern von Natvis, verwendet wird die `Size` Ausdruck in einem [ArrayItems-Erweiterung](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  

## <a name="natvis-views"></a>Natvis-Ansichten  

Sie können Natvis-Ansichten zum Anzeigen von Typen auf unterschiedliche Weise definieren. Hier ist z. B. eine Visualisierung der `std::vector` , definiert eine vereinfachte Ansicht, die mit dem Namen `simple`. Die `DisplayString` und `ArrayItems` Elemente, die in der Standardansicht angezeigt und die `simple` anzeigen, während die `[size]` und `[capacity]` Elemente nicht angezeigt, der `simple` anzeigen. 

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  


In der **Watch** Fenster verwenden die **, Ansicht** Formatbezeichner, um eine alternative Ansicht anzugeben. Die einfache Ansicht angezeigt wird, als **vec,view(simple)**:  

![Überwachungsfenster mit einfacher Ansicht](../debugger/media/watch-simpleview.png "Überwachungsfenster mit einfacher Ansicht")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis-Fehlern  

Wenn der Debugger Fehler in einem visualisierungseintrag feststellt, wird sie ignoriert. Es zeigt den Typ in unformatierter Form an oder wählt eine andere geeignete Visualisierung. Sie können Natvis-Diagnose verwenden, zu verstehen, warum der Debugger einen visualisierungseintrag ignoriert und das zugrunde liegende Syntax finden in und ausdrucksanalysefehler angezeigt. 

**Natvis-Diagnose aktivieren:**

- Klicken Sie unter **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen**  >  **Fenster "Ausgabe"** legen **Natvis-diagnosemeldungen (nur C++)** zu **Fehler**, **Warnung**, oder  **Ausführliche**, und wählen Sie dann **OK**. 

Die Fehler erscheinen in der **Ausgabe** Fenster.  

##  <a name="BKMK_Syntax_reference"></a> Natvis-Syntaxverweis  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer-Element  
Bei dem `AutoVisualizer`-Element handelt es sich um den Stammknoten der *NATVIS*-Datei, der das `xmlns:`-Attribut für den Namespace enthält. 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

Die `AutoVisualizer` -Element kann entweder [Typ](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), und ["customvisualizer"](#BKMK_CustomVisualizer) untergeordneten Elemente. 

###  <a name="BKMK_Type"></a> Type-Element  

Eine grundlegende `Type` sieht wie im folgenden Beispiel:  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 Die `Type` -Element gibt an:  

1. Art die Visualisierung für verwendet werden soll (die `Name` Attribut).  
   
2. Wie der Wert eines Objekts dieses Typs aussehen soll (das `DisplayString` -Element).  
   
3. Was die Member des Typs aussehen sollen, wenn der Benutzer den Typ in einem Variablen Fenster Erweitert (der `Expand` Knoten).  
   
#### <a name="templated-classes"></a>Auf Vorlagen basierende Klassen
Die `Name` Attribut der `Type` -Elements kann ein Sternchen `*` als Platzhalterzeichen, das für vorlagenbasierte Klassennamen verwendet werden kann.  

Im folgenden Beispiel wird der gleichen Visualisierung kennen, ob das Objekt verwendet einen `CAtlArray<int>` oder `CAtlArray<float>`. Es ist für ein bestimmten visualisierungseintrag eine `CAtlArray<float>`, und klicken Sie dann dieses Vorrang vor dem generischen Objekt hat.  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

Sie können Vorlagenparameter im visualisierungseintrag verwiesen, mithilfe von Makros "$t1", $T2, und so weiter. Beispiele zu diesen Makros finden Sie in den *NATVIS*-Dateien, die in Visual Studio bereitgestellt werden.  

####  <a name="BKMK_Visualizer_type_matching"></a> Typenabgleich in der Schnellansicht  
Wenn ein visualisierungseintrag nicht überprüft, wird die nächste verfügbare Visualisierung verwendet.  

#### <a name="inheritable-attribute"></a>Inheritable-Attribut  
Der optionale `Inheritable` Attribut gibt an, ob eine Visualisierung nur für einen Basistyp gilt oder auf einen Basistyp und alle Typen abgeleiteten. Der Standardwert von `Inheritable` ist `true`.  

Im folgenden Beispiel gilt die Visualisierung nur für die `BaseClass` Typ:  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Priority-Attribut  

Der optionale `Priority` -Attribut gibt die Reihenfolge, in denen alternative Definitionen verwendet, wenn eine Definition kann nicht analysiert werden. Die möglichen Werte der `Priority` sind: `Low`, `MediumLow`,`Medium`, `MediumHigh`, und `High`. Der Standardwert ist `Medium`sein. Die `Priority` -Attribut unterscheidet nur zwischen Prioritäten in derselben *natvis* Datei.  

Im folgende Beispiel analysiert zuerst den Eintrag, der die 2015 STL entspricht. Schlägt dies fehl, analysiert, wird den alternativen Eintrag für die 2013-Version von STL verwendet:  

```xml
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  

<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  

### <a name="optional-attribute"></a>Optional-Attribut  
Sie können Einfügen einer `Optional` Attribut auf einen beliebigen Knoten. Ein Teilausdruck in einem optionalen Knoten nicht analysiert werden, der Debugger ignoriert diesen Knoten, aber gilt die restlichen den `Type` Regeln. Im folgenden Typ ist `[State]` nicht optional, während `[Exception]` jedoch optional ist.  Wenn `MyNamespace::MyClass` verfügt über ein Feld mit dem Namen _`M_exceptionHolder`sowohl die `[State]` Knoten und die `[Exception]` Knoten angezeigt, aber wenn keine `_M_exceptionHolder` Feld nur die `[State]` Knoten angezeigt wird.

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Condition-Attribut  

Der optionale `Condition` Attribut ist für viele visualisierungselemente verfügbar und gibt an, wann eine visualisierungsregel verwendet. Wenn der Ausdruck im Condition-Attribut ergibt `false`, die visualisierungsregel nicht angewendet. Ergibt die Auswertung `true`, oder es ist keine `Condition` -Attribut, auf die Visualisierung angewendet wird. Sie können dieses Attribut für die If-else-Logik in den visualisierungseinträgen verwenden. 

Die folgende Visualisierung verfügt beispielsweise über zwei `DisplayString` Elemente für den Typ eines intelligenten Zeigers. Wenn die `_Myptr` Element leer ist, die Bedingung des ersten `DisplayString` Element aufgelöst wird, um `true`, sodass dieses Formular wird angezeigt. Wenn die `_Myptr` Member nicht leer ist, ergibt die Bedingung `false`, und das zweite `DisplayString` Element anzeigt.  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView- und ExcludeView-Attribute  

Die `IncludeView` und `ExcludeView` Attribute geben Elemente angezeigt oder in bestimmten Ansichten nicht angezeigt. Z. B. in der folgenden Natvis-Spezifikation von `std::vector`, `simple` Ansicht nicht angezeigt. die `[size]` und `[capacity]` Elemente.

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

Sie können die `IncludeView` und `ExcludeView` Attribute auf Typen und einzelne Member.  

###  <a name="BKMK_Versioning"></a> Version-Element  
Die `Version` Element festlegt, einen visualisierungseintrag auf ein bestimmtes Modul und eine Version. Die `Version` Element können Namenskonflikte zu vermeiden, unbeabsichtigter Konflikte reduziert und ermöglicht eine andere Visualisierungen für unterschiedliche Versionen.  

Wenn es sich bei eine allgemeinen Headerdatei, die von anderen Modulen verwendet wird, ein Typ definiert, wird die Visualisierung mit Versionsangaben nur, wenn der Typ in der angegebenen Version ist.  

Im folgenden Beispiel gilt die Visualisierung nur für die `DirectUI::Border` Typ finden Sie in der `Windows.UI.Xaml.dll` von Version 1.0 bis 1.5. 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> DisplayString-element 
Die `DisplayString` Element gibt eine Zeichenfolge, die als der Wert einer Variablen angezeigt. Beliebige Zeichenfolgen können mit Ausdrücken gemischt werden. Sämtliche Inhalte innerhalb von geschweiften Klammern werden als ein Ausdruck interpretiert. Z. B. die folgenden `DisplayString` Eintrag:  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

Bedeutet, dass Variablen des Typs `CPoint` wie in dieser Abbildung angezeigt:  

 ![Verwenden eines DisplayString-Elements](../debugger/media/dbg_natvis_cpoint_displaystring.png "Verwenden eines DisplayString-Elements")  

In der `DisplayString` Ausdruck `x` und `y`, die Mitglieder der sind `CPoint`, werden in geschweiften Klammern, sodass ihre Werte ausgewertet werden. Das Beispiel zeigt auch, wie Sie eine geschweifte Klammer mit Escapezeichen versehen können mithilfe von doppelten geschweiften Klammern ( `{{` oder `}}` ).  

> [!NOTE]
> Das `DisplayString` -Element ist das einzige Element, das beliebige Zeichenfolgen und die Syntax mit geschweiften Klammern akzeptiert. Alle anderen visualisierungselemente akzeptieren nur Ausdrücke, die vom Debugger ausgewertet werden kann.  

###  <a name="BKMK_StringView"></a> StringView-element 

Die `StringView` -Element definiert einen Wert, der der Debugger an die integrierte Text-Schnellansicht gesendet werden kann. Angenommen, die folgende Visualisierung für die `ATL::CStringT` Typ:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

Die `CStringT` Objekt in einem Variablenfenster wie im folgenden Beispiel angezeigt:   

![CStringT-DisplayString-Elements](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT-DisplayString-Element")  

Hinzufügen einer `StringView` Element weist den Debugger können sie den Wert als eine textvisualisierung angezeigt.  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

Während des Debuggens können Sie das Lupensymbol neben der Variablen auswählen, und wählen Sie dann **Text-Schnellansicht** zur Anzeige der Zeichenfolge, die **M_pszData** verweist auf.  

 ![CStringT-Daten mit StringView-Schnellansicht](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT-Daten mit StringView-Schnellansicht")  

Der Ausdruck `{m_pszData,su}` enthält C++-Formatbezeichner **"su"**, um den Wert als Unicode-Zeichenfolge anzuzeigen. Weitere Informationen finden Sie unter [Formatbezeichner in C++](../debugger/format-specifiers-in-cpp.md).  

###  <a name="BKMK_Expand"></a> Element erweitern 

Der optionale `Expand` Knoten passt die untergeordneten Elemente eines Typs visualisiert, wenn Sie den Typ in einem Variablenfenster erweitern. Die `Expand` Knoten akzeptiert eine Liste von untergeordneten Knoten, die die untergeordneten Elemente zu definieren.  

- Wenn ein `Expand` Knoten nicht die untergeordneten Elemente verwenden Sie die Regeln für die Erweiterung in einem visualisierungseintrag angegeben.  
  
- Wenn ein `Expand` mit ohne untergeordnete Knoten, Knoten angegeben wird, der Typ ist nicht in den Debuggerfenstern erweiterbar.  

####  <a name="BKMK_Item_expansion"></a> Item-Erweiterung  

 Die `Item` -Element ist die einfache und geläufige Element in einer `Expand` Knoten. Das`Item` -Element definiert ein einzelnes untergeordnetes Element. Z. B. eine `CRect` Klasse mit Feldern `top`, `left`, `right`, und `bottom` hat den folgenden visualisierungseintrag:  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

Im Debuggerfenster die `CRect` Typ sieht wie im folgenden Beispiel aus:  

![CRect mit Item-Element-Erweiterung](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect mit Item-Element-Erweiterung")  

Der Debugger wertet die angegebenen Ausdrücken die `Width` und `Height` Elemente und zeigt die Werte in der **Wert** Spalte der Variablenfenster. 

Der Debugger erstellt automatisch die **[Rohdatenansicht]** Knoten für jede benutzerdefinierte Erweiterung. Der obige Screenshot zeigt die **[Rohdatenansicht]** Knoten erweitert, um anzuzeigen, wie die Standard-Rohdatenansicht des Objekts von der Natvis-Visualisierung unterscheidet. Die standarderweiterung erstellt eine Teilstruktur für die Basisklasse und alle Datenmember der Basisklasse als untergeordnete Elemente aufgeführt.  

> [!NOTE]
> Wenn der Ausdruck des Item-Elements auf einen komplexen Typ weist die **Element** -Knoten selbst erweiterbar ist.  

####  <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion  
Verwenden Sie den `ArrayItems` -Knoten, damit der Visual Studio-Debugger den Typ als Array interpretieren und die einzelnen Elemente anzeigen kann. Die Visualisierung für `std::vector` ist ein gutes Beispiel:  

```xml
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

Im `std::vector` -Knoten werden die einzelnen Elemente angezeigt, wenn sie im Variablenfenster erweitert werden:  

![Std:: Vector mit ArrayItems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "Std:: Vector mit ArrayItems-Erweiterung")  

Die `ArrayItems` Knoten benötigen:  

- Einen `Size`-Ausdruck (der als ganze Zahl ausgewertet werden muss), damit der Debugger die Länge des Arrays kennt.  
- Ein `ValuePointer` Ausdruck, der auf das erste Element verweist (die einen Zeiger eines Elementtyps, der nicht sein muss `void*`).  

Der Standardwert mit der Arrayuntergrenze lautet „0“. Um den Wert zu überschreiben, verwenden eine `LowerBound` Element. Die *natvis* Dateien, die mit Visual Studio bereitgestellt haben, Beispiele.  

>[!NOTE]
>Können Sie die `[]` -Operator, z. B. `vector[i]`, mit jeder beliebigen Visualisierung von eindimensionales Array, das verwendet `ArrayItems`, auch wenn der Typ selbst (z. B. `CATLArray`) lässt sich nicht auf diesen Operator.  

Sie können auch auf mehrdimensionale Arrays angeben. In diesem Fall benötigt der Debugger etwas mehr Informationen an die untergeordneten Elemente ordnungsgemäß angezeigt:  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

- `Direction` Gibt an, ob das Array in zeilengerichteter oder spaltengerichteter Reihenfolge ist. 
- `Rank` gibt den Rang des Arrays an. 
- Das `Size`-Element akzeptiert den impliziten `$i`-Parameter, der durch den Dimensionsindex ersetzt wird, um die Länge des Arrays in dieser Dimension festzustellen. Im vorherigen Beispiel ist der Ausdruck `_M_extent.M_base[0]` soll die Länge der 0. Dimension `_M_extent._M_base[1]` den 1. und So weiter.  

Hier wird gezeigt, wie es ein zweidimensionales `Concurrency::array` Objekt im Debuggerfenster aussieht:  

![Zweidimensionales Array mit ArrayItems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "zweidimensionales Array mit ArrayItems-Erweiterung")  

####  <a name="BKMK_IndexListItems_expansion"></a> IndexListItems-Erweiterung  

Sie können `ArrayItems` Erweiterung nur dann, wenn die Arrayelemente im Arbeitsspeicher zusammenhängend angeordnet sind. Der Debugger erreicht das nächste Element durch ihr Zeiger auf die einfach zu erhöhen. Wenn den Index für Wertknoten bearbeitet werden muss, verwenden Sie `IndexListItems` Knoten. Hier ist eine Visualisierung mit einer `IndexListItems` Knoten:  

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  
```  

Der einzige Unterschied zwischen `ArrayItems` und `IndexListItems` ist die `ValueNode`, die den vollständigen Ausdruck für das i erwartet<sup>th</sup> Element mit dem impliziten `$i` Parameter.  

>[!NOTE]
>Können Sie die `[]` -Operator, z. B. `vector[i]`, mit jeder beliebigen Visualisierung von eindimensionales Array, das verwendet `IndexListItems`, auch wenn der Typ selbst (z. B. `CATLArray`) lässt sich nicht auf diesen Operator.  

####  <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems-Erweiterung  

Wenn der Schnellansichtstyp eine verknüpfte Liste darstellt, kann der Debugger die untergeordneten Elemente mithilfe eines `LinkedListItems` -Knotens anzeigen. Die folgende Visualisierung für die `CAtlList` -Typ verwendet `LinkedListItems`:  

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  
```  

Das `Size` -Element bezieht sich auf die Länge der Liste. `HeadPointer` zeigt auf das erste Element, `NextPointer` bezieht sich auf das nächste Element, und `ValueNode` verweist auf den Wert des Elements.  

Der Debugger wertet den `NextPointer` und `ValueNode` Ausdrücke im Rahmen der `LinkedListItems` Node-Element, nicht des übergeordneten Listentyps. Im vorherigen Beispiel `CAtlList` verfügt über eine `CNode` Klasse (finden Sie im `atlcoll.h`), der ein Knoten der verknüpften Liste. `m_pNext` und `m_element` sind Felder dieser `CNode` -Klasse, nicht die `CAtlList` Klasse.  

`ValueNode` kann leer gelassen werden, oder verwenden Sie `this` zum Verweisen auf die `LinkedListItems` Knoten selbst.  

#### <a name="customlistitems-expansion"></a>CustomListItems-Erweiterung  
Die `CustomListItems` -Erweiterung ermöglicht Ihnen das Schreiben von benutzerdefinierter Logik für das Traversieren einer Datenstruktur, beispielsweise einer Hashtabelle. Verwenden Sie `CustomListItems` passen Sie zum Visualisieren von Datenstrukturen, die C++-Ausdrücke für alles verwenden können, müssen Sie bewerten, aber nicht sehr, wirklich für `ArrayItems`, `IndexListItems`, oder `LinkedListItems`.  

Die folgenden Schnellansicht für `CAtlMap` ist ein ausgezeichnetes Beispiel, in denen `CustomListItems` eignet.  

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  

        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

Können Sie `Exec` zum Ausführen von Code in der ein `CustomListItems` Erweiterung mithilfe von Variablen und Objekte, die in der Erweiterung definiert. Sie können logische Operatoren, arithmetische Operatoren und Zuweisungsoperatoren mit `Exec`. Sie können keine `Exec` Funktionen ausgewertet.

`CustomListItems` unterstützt die folgenden systeminternen Funktionen:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> TreeItems-Erweiterung  
 Wenn der Schnellansichtstyp eine Struktur darstellt, kann der Debugger die Struktur durchlaufen und seine untergeordneten Elemente mithilfe eines `TreeItems` -Knotens anzeigen. Hier ist die Visualisierung für die `std::map` mittels einer `TreeItems` Knoten:  

```xml
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  
```  

Die Syntax ähnelt der `LinkedListItems` Knoten. `LeftPointer`, `RightPointer`, und `ValueNode` werden im Kontext der strukturknotenklasse ausgewertet. `ValueNode` kann leer gelassen werden, oder verwenden Sie `this` zum Verweisen auf die `TreeItems` Knoten selbst.  

####  <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem-Erweiterung  
 Die `ExpandedItem` Element generiert eine aggregierte untergeordnete Ansicht, indem Sie die Eigenschaften der Basisklasse oder Elemente anzeigen, als ob sie untergeordnete Elemente des schnellansichtstyps wären. Der Debugger wertet den angegebenen Ausdruck und die untergeordneten Knoten des Ergebnisses an die untergeordnete Liste des schnellansichtstyps angefügt. 

Z. B. der Typ des intelligenten Zeigers `auto_ptr<vector<int>>` zeigt in der Regel als:  

 ![automatische&#95;Ptr&#60;Vektor&#60;Int&#62; &#62; standarderweiterung](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Standarderweiterung")  

 Um die Werte des Vektors anzuzeigen, müssen Sie zwei Ebenen im Variablenfenster, durchläuft einen Drilldown der `_Myptr` Member. Durch Hinzufügen eines `ExpandedItem`-Elements können Sie die `_Myptr`-Variable aus der Hierarchie ausschließen und die Vektorelemente direkt anzeigen:  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![automatische&#95;Ptr&#60;Vektor&#60;Int&#62; &#62; ExpandedItem-Erweiterung](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem-Erweiterung")  

Das folgende Beispiel zeigt, wie Sie Eigenschaften aus der Basisklasse in einer abgeleiteten Klasse zu aggregieren. Angenommen, die `CPanel` -Klasse wird von `CFrameworkElement`abgeleitet. Anstatt zu wiederholen die Eigenschaften, die von der Basisklasse stammen `CFrameworkElement` -Klasse, die `ExpandedItem` Knoten Visualisierung fügt diese Eigenschaften an die untergeordnete Liste des der `CPanel` Klasse. 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

Der **nd**-Formatbezeichner, mit dem die Visualisierungsabstimmung für die abgeleitete Klasse deaktiviert wird, ist hier erforderlich. Andernfalls den Ausdruck `*(CFrameworkElement*)this` würde dazu führen, dass die `CPanel` Visualisierung aus, um erneut angewendet werden, da die für die visualisierungstypenabstimmung Abgleichsregeln halten es für die geeignetste angesehen. Verwenden Sie die **Nd** Formatbezeichner um anzuweisen, den Debugger an die basisklassenvisualisierung oder die standarderweiterung zu verwenden, wenn die Basisklasse keine Visualisierung hat.  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Synthetische Elementerweiterung  
 Während das `ExpandedItem`-Element eine flachere Datenansicht durch die Beseitigung von Hierarchien bereitstellt, bewirkt der `Synthetic`-Knoten das Gegenteil. Sie können ein künstliches untergeordnetes Element zu erstellen, die ein Ergebnis eines Ausdrucks nicht ist. Das künstliche Element haben untergeordnete Elemente des eigenen. Im folgenden Beispiel verwendet die Visualisierung für den `Concurrency::array` -Typ einen `Synthetic` -Knoten, um dem Benutzer eine Diagnosemeldung anzuzeigen:  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  
```  

 ![Concurrency:: Array mit synthetischen Element-Erweiterung](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: Array mit synthetischen Element-Erweiterung")  

###  <a name="BKMK_HResult"></a> HResult-element 
 Die `HResult` Element können Sie anpassen, die für die angezeigten Informationen eine **HRESULT** in Debuggerfenstern. Das `HRValue`-Element muss den 32-Bit-Wert des anzupassenden **HRESULT**-Elements enthalten. Die `HRDescription` -Element enthält die Informationen im Debuggerfenster angezeigt.  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer-Elements 
Ein `UIVisualizer` -Element registriert ein grafisches Schnellansichts-Plug-In mit dem Debugger. Ein grafisches Schnellansichts erstellt ein Dialogfeld oder ein anderes Oberflächenelement, die eine Variable oder ein Objekt auf eine Weise konsistent mit dem Datentyp anzeigt. Die Schnellansicht-Plug-in erstellt werden muss, als eine [VSPackage](../extensibility/internals/vspackages.md), und Sie müssen einen Dienst verfügbar machen, die der Debugger nutzen können. Die *natvis* Datei enthält Registrierungsinformationen für das plug-in, z. B. den Namen, die GUID des verfügbar gemachten Diensts und die Typen, die sie visualisieren kann.  

Im Folgenden ist ein Beispiel eines UIVisualizer-Elements angegeben:  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  

- Ein `ServiceId`  -  `Id` -Paar des Attributs identifiziert eine `UIVisualizer`. Die `ServiceId` ist die GUID des Diensts die Schnellansicht Paket verfügbar macht. `Id` ist ein eindeutiger Bezeichner, der Schnellansichten, unterscheidet, wenn ein Dienst mehrere bereitstellt. Im vorherigen Beispiel enthält der gleiche schnellansichtsdienst zwei Schnellansichten bereit.  
  
- Die `MenuName` Attribut definiert eine Schnellansicht-Name, der in der Dropdownliste neben dem Lupensymbol im Debugger angezeigt. Beispiel:  

  ![Kontextmenü für UIVisualizer-Menü](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer-Menü-Kontextmenü")  

Alle Typen, die der *natvis* Datei muss explizit auflisten alle Benutzeroberflächen-Schnellansichten, die sie anzeigen können. Der Debugger passt die schnellansichtsverweise in den typeinträgen mit den registrierten Schnellansichten. Z. B. die folgenden typeintrag für `std::vector` Verweise der `UIVisualizer` im vorherigen Beispiel.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Sehen Sie ein Beispiel für eine `UIVisualizer` in die [Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) Erweiterung, die zum Anzeigen von Bitmaps im Speicher verwendet. 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer-Element  
 `CustomVisualizer` ist ein Erweiterungspunkt, der eine VSIX-Erweiterung, die Sie schreiben angibt, um Visualisierungen in Visual Studio-Code zu steuern. Weitere Informationen zum Schreiben von VSIX-Erweiterungen finden Sie unter den [Visual Studio SDK](../extensibility/visual-studio-sdk.md). 

Es ist viel aufwendiger als eine XML-Natvis-Definition eine benutzerdefinierte Schnellansicht schreiben, jedoch steht Ihnen frei von Einschränkungen zu Natvis Funktionsweise oder Bedeutung nicht unterstützt. Benutzerdefinierte Schnellansichten haben Zugriff auf den vollständigen Satz der Debugger-Erweiterbarkeits-APIs, die Abfragen und Ändern des debuggenden Prozesses oder die Kommunikation mit anderen Teilen von Visual Studio.  

 Sie können die `Condition`, `IncludeView`, und `ExcludeView` Attribute `CustomVisualizer` Elemente.
