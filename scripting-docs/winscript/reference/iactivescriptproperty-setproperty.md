---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty-Methode, IActiveScriptProperty-Schnittstelle"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
Legt die Eigenschaft fest, die vom Parameter angegeben wird.  
  
## Syntax  
  
```  
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### Parameter  
 `dwProperty`  
 Der Wert, auf den die Eigenschaft festgelegt werden soll.  
  
 `pvarIndex`  
 Wird nicht verwendet.  
  
 `pvarValue`  
 Der Wert der Eigenschaft.  
  
 Die Werte, die für `dwProperty` zulässig sind, werden in der folgenden Tabelle beschrieben.  
  
|Konstante|Wert|Bedeutung|  
|---------------|----------|---------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Erzwingt das Skriptmodul, um im Modus anstelle des Gleitkommamodus aufzuteilen.  Der Standardwert ist `False`.|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|Ermöglicht die Zeichenfolgencompare\-funktion des Skriptmoduls, ersetzt werden.|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|Informiert das Skriptmodul, dass keine anderen Skriptmodule vorhanden sein, um im globalen Objekt beizutragen.|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|Erzwingt das [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul, um einen Satz von unterstützt werden, Sprachfunktionen auszuwählen.  Der Standardsatz von den Sprachfunktionen, die vom [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul unterstützt werden, ist zur festgelegten Sprachfunktion entsprechend, die in Version 5.7 des [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmoduls angezeigt.|  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument ist ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
  
## Hinweise  
 So ganzzahlige Division, Aufruf `SetProperty` aktivieren oder deaktivieren und `Boolean` zu `Object` konvertieren.  Standardmäßig ist der Eigenschaftswert `False`.  Wenn Sie festlegen `True`, Divisionen nur ganze Zahlen zurückgeben.  
  
 So benutzerdefinierten Zeichenfolgenvergleich, Aufruf `SetProperty` und in einem `Object`\-Wert aktivieren oder deaktivieren.  Das Objekt, das Sie in übergeben, muss die Schnittstelle [IActiveScriptStringCompare\-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md) implementieren.  Die [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md)\-Methode der [IActiveScriptStringCompare\-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md)\-Schnittstelle wird jedes Mal aufgerufen, dass eine Zeichenfolgencompare\-funktion ausgeführt wird.  
  
 Um den von unterstützt werden Sprachfunktionen auszuwählen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wenn das Skriptmodul initialisiert wird, rufen Sie `SetProperty` auf und übergeben Sie einen Wert der zur Sprachfunktion entspricht, die festgelegt wird für SCRIPTPROP\_INVOKEVERSIONING aktiviert werden.  Wenn diese Eigenschaft auf 1 \(SCRIPTLANGUAGEVERSION\_5\_7\) festgelegt ist, sind die verfügbaren Sprachfunktionen identisch, die die, die in Version 5.7 des [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmoduls angezeigt.  Wenn es auf 2 \(SCRIPTLANGUAGEVERSION\_5\_8\) festgelegt ist, sind die verfügbaren Sprachfeatures, die in Version 5.7 zusätzlich zu den neuen Funktionen angezeigt, die in Version 5.8 hinzugefügt wurden.  Diese Eigenschaft ist standardmäßig auf 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\) festgelegt, das der festgelegten Sprachfunktion entspricht, die in Version 5.7 ist, es sei denn, der Host ein anderes Standardverhalten unterstützt.  Beispielsweise entscheidet Internet Explorer 8 in die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Sprachfunktionen, die vom [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul der Version 5.8 standardmäßig unterstützt werden, wenn der Standardwert Dokumente für Internet Explorer 8 "Internet Explorer 8\-Standard" Modus ist.  Das Wechseln des Internet Explorer 8\-Dokumentenmodus an Internet Explorer 7\-Standards oder \-Quirksmodus macht das Skriptmodul [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zurück, um die festgelegte Sprachfunktion zu unterstützen, die nur im [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul der Version 5.7 vorhanden war.  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING sollte nur festgelegt werden, wenn das [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul initialisiert wird.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie das Skriptmodul erzwingt, um ganzzahlige Division verwenden und wie Überladen der Compare\-Funktion zulässig.  
  
```csharp  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## Siehe auch  
 [Definieren von Dokumenten\-Kompatibilität](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)