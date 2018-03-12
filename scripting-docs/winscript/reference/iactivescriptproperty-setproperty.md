---
title: IActiveScriptProperty::SetProperty | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Legt die Eigenschaft, die durch den Parameter angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
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
|SCRIPTPROP_INTEGERMODE|0x00003000|Erzwingt, dass das Skriptmodul im Modus ganze Zahl, anstelle von unverankerten Modus aufteilen. Der Standardwert ist `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Kann die Zeichenfolge vergleichen-Funktion des verwendeten Skriptmoduls ersetzt werden.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informiert das Skriptmodul, das keine anderen Skriptmodule vorhanden sein, um auf das globale Objekt beitragen.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Erzwingt, dass die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul zum Auswählen eines Satzes von Funktionen der Programmiersprache unterstützt werden müssen. Der Standardsatz von Sprachfunktionen, die von unterstützt die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul entspricht den Satz von Sprache, die in Version 5.7 angezeigt wurden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument ist ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie zum Aktivieren oder Deaktivieren der ganzzahligen Division, `SetProperty` , und konvertieren Sie eine `Boolean` auf eine `Object`. Standardmäßig ist der Eigenschaftswert `False`. Wenn Sie die Einstellung `True`, Divisionen nur ganze Zahlen zurück.  
  
 Rufen Sie zum Aktivieren oder Deaktivieren von benutzerdefinierten Zeichenfolgenvergleich, `SetProperty` auf und übergeben ein `Object` Wert. Das Objekt, das Sie übergeben, muss die Schnittstelle implementieren [IActiveScriptStringCompare-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md). Die [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) Methode der [IActiveScriptStringCompare-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md) Schnittstelle wird jedes Mal aufgerufen, die eine Zeichenfolge vergleichen-Funktion ausgeführt wird.  
  
 Wählen Sie den Satz von Sprachfunktionen, wenn unterstützt werden müssen die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul initialisiert wird, rufen Sie `SetProperty` und übergeben Sie einen Wert, der an die Sprachfunktion, legen Sie für SCRIPTPROP_INVOKEVERSIONING aktiviert werden soll. Wenn diese Eigenschaft auf 1 (SCRIPTLANGUAGEVERSION_5_7) festgelegt ist, die verfügbaren Sprachfunktionen sind identisch mit denen, die in Version 5.7 angezeigt wurden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul. Wenn es auf 2 (SCRIPTLANGUAGEVERSION_5_8) festgelegt ist, werden die verfügbaren Sprachen-Funktionen, die in Version 5.7 zusätzlich zu den neuen Features angezeigt, die in Version 5.8 hinzugefügt wurden. Standardmäßig ist diese Eigenschaft auf 0 (SCRIPTLANGUAGEVERSION_DEFAULT), festgelegt Dies entspricht den Satz von Sprache, der in Version 5.7, angezeigt wurden, wenn der Host einem anderen Standardverhalten unterstützt. Z. B. Internet Explorer 8 "OPTS" in der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Sprachfunktionen, die von der Version 5.8 unterstützt werden [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul Standard, wenn der Dokument-Standardmodus von Internet Explorer 8 "Internet Explorer 8 (Standardmodus)" Modus ist. Umschalten zwischen der Dokumentmodus für Internet Explorer 8, Internet Explorer 7 (Standardmodus) oder im Quirksmodus setzt die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul unterstützt nur die Sprache Funktionsgruppe, die vorhanden waren in der Version 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING sollte festgelegt werden, nur, wenn die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul initialisiert wird.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie das Skriptmodul in Ganzzahldivision verwenden erzwingen und ermöglichen das Überladen von der Compare-Funktion.  
  
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
 [Definieren der Dokumentkompatibilität](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)