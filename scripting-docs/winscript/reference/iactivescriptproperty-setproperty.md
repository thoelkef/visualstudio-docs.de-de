---
title: 'Iactivescriptproperty:: SetProperty | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571310"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Legt die-Eigenschaft fest, die durch den-Parameter angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwProperty`  
 Der festzulegende Eigenschaftswert.  
  
 `pvarIndex`  
 Nicht verwendet.  
  
 `pvarValue`  
 Der Wert der Eigenschaft.  
  
 Die für `dwProperty` zulässigen Werte werden in der folgenden Tabelle beschrieben.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Erzwingt das Aufteilen der Skript-Engine im ganzzahligen Modus anstelle des Gleit Komma Modus. Der Standardwert ist `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Ermöglicht das Ersetzen der Zeichen folgen Vergleichsfunktion der Skript-Engine.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Teilt der Skript-Engine mit, dass keine anderen Skript-Engines vorhanden sind, um zum globalen Objekt beizutragen.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Erzwingt, dass die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine eine Reihe von sprach Features auswählen muss, die unterstützt werden sollen. Der Standardsatz von sprach Features, die von der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine unterstützt werden, entspricht dem sprach Featuresatz, der in Version 5,7 des [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Scripting Engine enthalten war.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument ist ungültig.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Zum Aktivieren oder Deaktivieren der ganzzahligen Division rufen Sie `SetProperty` auf, und konvertieren Sie eine `Boolean` in eine `Object`. Standardmäßig ist der Eigenschafts Wert `False`. Wenn Sie den Wert auf `True`festlegen, werden bei Divisions Vorgängen nur ganze Zahlen zurückgegeben.  
  
 Rufen Sie zum Aktivieren oder Deaktivieren des benutzerdefinierten Zeichen folgen Vergleichs `SetProperty` auf, und übergeben Sie einen `Object`-Wert. Das Objekt, das Sie übergeben, muss die Schnittstelle [iactivescriptstringcompare-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md)implementieren. Die [Methode "](../../winscript/reference/iactivescriptstringcompare-strcomp.md) -Methode" der [iactivescriptstringcompare-Schnitt](../../winscript/reference/iactivescriptstringcompare-interface.md) Stelle wird jedes Mal aufgerufen, wenn eine Zeichen folgen Vergleichsfunktion ausgeführt wird.  
  
 Um die sprach Features auszuwählen, die bei der Initialisierung der Skript-Engine von [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] unterstützt werden sollen, rufen Sie `SetProperty` auf, und übergeben Sie einen Wert, der der sprach Funktionsgruppe entspricht, die für SCRIPTPROP_INVOKEVERSIONING aktiviert werden soll. Wenn diese Eigenschaft auf 1 (SCRIPTLANGUAGEVERSION_5_7) festgelegt ist, sind die verfügbaren sprach Features identisch mit denen, die in Version 5,7 der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Skript-Engine aufgetreten sind. Wenn der Wert auf 2 (SCRIPTLANGUAGEVERSION_5_8) festgelegt ist, sind die verfügbaren sprach Features neben den neuen Features, die in Version 5,8 hinzugefügt wurden, in Version 5,7 enthalten. Standardmäßig ist diese Eigenschaft auf 0 (SCRIPTLANGUAGEVERSION_DEFAULT) festgelegt, was dem sprach Funktions Satz entspricht, der in Version 5,7 enthalten war, es sei denn, der Host unterstützt ein anderes Standardverhalten. Internet Explorer 8 wird z. b. in den [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sprach Features, die von der Version 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine unterstützt werden, standardmäßig aktiviert, wenn der Standarddokument Modus für Internet Explorer 8 der Internet Explorer 8-Standardmodus ist. Wenn Sie den Internet Explorer 8-Dokument Modus auf Internet Explorer 7-Standards oder den Quiri-Modus umstellen, wird die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Skript-Engine zurückgesetzt, sodass nur der sprach Featuresatz unterstützt wird, der in Version 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Scripting Engine  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING sollte nur festgelegt werden, wenn die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Skript-Engine initialisiert wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie erzwingen können, dass die Skript-Engine die ganzzahlige Division verwendet und das Überladen der Vergleichsfunktion zulässt.  
  
```c#  
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
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Dokument Kompatibilitäts](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)