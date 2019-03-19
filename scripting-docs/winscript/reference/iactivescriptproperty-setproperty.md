---
title: IActiveScriptProperty::SetProperty | Microsoft-Dokumentation
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
ms.openlocfilehash: f24f63612b5d4dcb1c6a5a65e0ad38f8056cf842
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159386"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Legt die Eigenschaft, die durch den Parameter angegeben wird.  
  
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
  
 Die Werte für zulässige `dwProperty` werden in der folgenden Tabelle beschrieben.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Erzwingt, dass die Skript-Engine, um im Modus ganze Zahl, anstelle von unverankerten Modus zu unterteilen. Der Standardwert ist `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Ermöglicht der String-Compare-Funktion des verwendeten Skriptmoduls ersetzt werden.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informiert die Skript-Engine, die keine andere Skript-Engines vorhanden sind, um auf das globale Objekt beitragen.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Erzwingt, dass die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine, wählen Sie einen Satz von Sprachfeatures unterstützt werden müssen. Der Standardsatz von Sprachfunktionen, die von unterstützt die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine entspricht den Funktionsumfang, die in Version 5.7 von angezeigt wurden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument ist ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie zum Aktivieren oder Deaktivieren der Division ganzer Zahlen, `SetProperty` und konvertieren eine `Boolean` auf eine `Object`. Standardmäßig ist der Eigenschaftswert `False`. Wenn Sie die Einstellung `True`, divisionsvorgängen nur ganze Zahlen zurück.  
  
 Rufen Sie zum Aktivieren oder Deaktivieren von benutzerdefinierten Zeichenfolgenvergleich, `SetProperty` und übergeben Sie ein `Object` Wert. Das Objekt, das Sie übergeben, muss die Schnittstelle implementieren [IActiveScriptStringCompare-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md). Die [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) Methode der [IActiveScriptStringCompare-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md) Schnittstelle wird jedes Mal aufgerufen, die eine String-Compare-Funktion ausgeführt wird.  
  
 Auswählen der Satz von Sprachfeatures, wenn unterstützt werden müssen die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine wird initialisiert, rufen `SetProperty` und übergeben Sie einen Wert, der an den Language Features für SCRIPTPROP_INVOKEVERSIONING aktiviert werden soll. Wenn diese Eigenschaft auf 1 (SCRIPTLANGUAGEVERSION_5_7) festgelegt ist, die verfügbaren Funktionen sind identisch mit denen, die in Version 5.7 von angezeigt wurden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine. Wenn es auf 2 (SCRIPTLANGUAGEVERSION_5_8) festgelegt ist, sind die verfügbaren Funktionen, die in Version 5.7 neben neuen Features angezeigt, die Version 5.8 hinzugefügt wurden. Standardmäßig ist diese Eigenschaft auf 0 (SCRIPTLANGUAGEVERSION_DEFAULT), festgelegt; entspricht den Funktionsumfang, der in Version 5.7, angezeigt, wenn der Host ein Standardverhalten für verschiedene unterstützt. Z. B. Internet Explorer 8 "OPTS" in der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Sprachfunktionen, die von der Version 5.8 unterstützt werden [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine wird standardmäßig bei der Standard-Dokumentmodus für Internet Explorer 8 "Internet Explorer 8-Standards"-Modus ist. Umschalten zwischen der Dokumentmodus für Internet Explorer 8, Internet Explorer 7-Standards oder Quirks-Modus setzt die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine, unterstützen nur den Funktionsumfang, die vorhanden waren, in der Version 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING sollte festgelegt werden, nur, wenn die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine initialisiert wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Skript-Engine, mit der Division ganzer Zahlen zu erzwingen und zum Zulassen der Compare-Funktion überladen.  
  
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
 [Definieren der Dokumentkompatibilität](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)