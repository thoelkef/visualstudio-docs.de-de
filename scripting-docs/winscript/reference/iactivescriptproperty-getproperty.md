---
title: 'Iactivescriptproperty:: GetProperty | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571414"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Ruft die Eigenschaft ab, die durch den-Parameter angegeben wird.  
  
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
 Der Eigenschafts Wert, der angezeigt werden soll.  
  
 `pvarIndex`  
 Nicht verwendet.  
  
 `pvarValue`  
 Der Wert der Eigenschaft.  
  
 Die für `dwProperty` zulässigen Werte werden in der folgenden Tabelle beschrieben.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Erzwingt das Aufteilen der Skript-Engine im ganzzahligen Modus anstelle des Gleit Komma Modus.|  
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
 Der Host kann die SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION-Eigenschaft verwenden, um eine Skript-Engine darüber zu informieren, dass keine anderen Skript-Engines vorhanden sind, um zum globalen Objekt beizutragen. Internet Explorer kann z. b. die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Engine darüber informieren, dass die gerenderte Seite nur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skripts enthält. Folglich kann nur die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Engine dem globalen Objekt Fenster neue Eigenschaften hinzufügen, und es ist keine Visual Basic Scripting Edition (VBScript)-Engine vorhanden. Dieses Flag kann von der Engine ignoriert werden, oder es kann verwendet werden, um die Verwaltung von neuen Membern zu optimieren, die dem globalen Objekt hinzugefügt werden.  
  
 Der Host kann die SCRIPTPROP_INVOKEVERSIONING-Eigenschaft verwenden, um den Satz von sprach Features auszuwählen, der beim Starten der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine unterstützt werden soll. Wenn diese Eigenschaft auf 1 (SCRIPTLANGUAGEVERSION_5_7) festgelegt ist, sind die verfügbaren sprach Features identisch mit denen, die in Version 5,7 der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Skript-Engine aufgetreten sind. Wenn Sie auf 2 (SCRIPTLANGUAGEVERSION_5_8) festgelegt ist, sind die verfügbaren sprach Features neben den Features, die in Version 5,8 hinzugefügt wurden, in Version 5,7 enthalten. Standardmäßig ist diese Eigenschaft auf 0 (SCRIPTLANGUAGEVERSION_DEFAULT) festgelegt, was dem sprach Funktions Satz entspricht, der in Version 5,7 enthalten war, es sei denn, der Host unterstützt ein anderes Standardverhalten. Internet Explorer 8 unterstützt beispielsweise standardmäßig die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sprach Features, die von der Version 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skript-Engine unterstützt werden, wenn der Dokument Modus für Internet Explorer 8 der Internet Explorer 8-Standardmodus ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Dokument Kompatibilitäts](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))    
 [Iactivescriptproperty](../../winscript/reference/iactivescriptproperty.md) -   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)