---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Ruft die Eigenschaft, die durch den Parameter angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetProperty(  
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
 Der Eigenschaftswert abgerufen werden soll.  
  
 `pvarIndex`  
 Nicht verwendet.  
  
 `pvarValue`  
 Der Wert der Eigenschaft.  
  
 Die Werte für zulässige `dwProperty` werden in der folgenden Tabelle beschrieben.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Erzwingt, dass das Skriptmodul im Modus ganze Zahl, anstelle von unverankerten Modus aufteilen.|  
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
 Die SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION-Eigenschaft können der Host um ein Skriptmodul zu informieren, die keine anderen Skriptmodule vorhanden sein, um auf das globale Objekt beitragen. Z. B. Internet Explorer können Sie bestimmen, die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Modul, das die gerenderte Seite nur enthält [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skripts. Daher nur die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Modul kann neue Eigenschaften hinzufügen, für das globale Objektfenster, und es gibt kein Visual Basic Scripting Edition (VBScript)-Modul, um diesen Vorgang auszuführen. Das Modul kann ignorieren dieses Flag oder verwenden, um die Verwaltung der neuen Mitglieder zu optimieren, die auf das globale Objekt hinzugefügt werden.  
  
 Der Host kann mithilfe der Eigenschaft SCRIPTPROP_INVOKEVERSIONING wählen Sie den Satz von Sprachfunktionen, um werden unterstützt, wenn die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul gestartet wird. Wenn diese Eigenschaft auf 1 (SCRIPTLANGUAGEVERSION_5_7) festgelegt ist, die verfügbaren Sprachfunktionen sind identisch mit denen, die in Version 5.7 angezeigt wurden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul. Wenn es auf 2 (SCRIPTLANGUAGEVERSION_5_8) festgelegt ist, werden die verfügbaren Sprachen-Funktionen, die in Version 5.7 zusätzlich zu den Funktionen angezeigt, die in Version 5.8 hinzugefügt wurden. Standardmäßig ist diese Eigenschaft auf 0 (SCRIPTLANGUAGEVERSION_DEFAULT), festgelegt Dies entspricht den Satz von Sprache, der in Version 5.7, angezeigt wurden, wenn der Host einem anderen Standardverhalten unterstützt. Z. B. Internet Explorer 8 "OPTS" in der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Sprachfunktionen, die von der Version 5.8 unterstützt [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul Standard, wenn der Dokumentmodus für Internet Explorer 8-Modus "Internet Explorer 8 (Standardmodus)" ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren der Dokumentkompatibilität](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)