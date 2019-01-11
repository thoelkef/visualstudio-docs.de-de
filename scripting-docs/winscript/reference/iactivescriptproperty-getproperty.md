---
title: IActiveScriptProperty::GetProperty | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e68cb73b1b94b84d5133e1c7489bc8bf6309aea
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091298"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Ruft die Eigenschaft, die durch den Parameter angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
|SCRIPTPROP_INTEGERMODE|0x00003000|Erzwingt, dass die Skript-Engine, um im Modus ganze Zahl, anstelle von unverankerten Modus zu unterteilen.|  
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
 Der Host kann die SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION-Eigenschaft verwenden, um eine Skript-Engine darüber zu informieren, die keine andere Skript-Engines vorhanden sind, um auf das globale Objekt beitragen. Z. B. Internet Explorer informieren kann, die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Engine, die die gerenderte Seite nur enthält [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skripts. Daher nur die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Engine kann neue Eigenschaften hinzufügen, für das globale Objektfenster, und es gibt kein Modul Visual Basic Scripting Edition (VBScript) verwenden müssen. Die Engine kann ignorieren dieses Flag oder können sie um die Verwaltung von neuen Membern zu optimieren, die das globale Objekt hinzugefügt werden.  
  
 Der Host kann mithilfe der Eigenschaft SCRIPTPROP_INVOKEVERSIONING wählen Sie den Satz von Sprachfunktionen, um werden unterstützt, wenn die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine wird gestartet. Wenn diese Eigenschaft auf 1 (SCRIPTLANGUAGEVERSION_5_7) festgelegt ist, die verfügbaren Funktionen sind identisch mit denen, die in Version 5.7 von angezeigt wurden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine. Wenn es auf 2 (SCRIPTLANGUAGEVERSION_5_8) festgelegt ist, sind die verfügbaren Funktionen, die in Version 5.7 zusätzlich zu Funktionen angezeigt, die Version 5.8 hinzugefügt wurden. Standardmäßig ist diese Eigenschaft auf 0 (SCRIPTLANGUAGEVERSION_DEFAULT), festgelegt; entspricht den Funktionsumfang, der in Version 5.7, angezeigt, wenn der Host ein Standardverhalten für verschiedene unterstützt. Z. B. Internet Explorer 8 "OPTS" in der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Sprachfunktionen, die von der Version 5.8 unterstützt [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine wird standardmäßig bei der Dokumentmodus für Internet Explorer 8 "Internet Explorer 8-Standards"-Modus ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren der Dokumentkompatibilität](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)