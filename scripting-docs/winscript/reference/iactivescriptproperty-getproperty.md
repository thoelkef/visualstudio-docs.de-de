---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty-Methode, IActiveScriptProperty-Schnittstelle"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
Ruft die Eigenschaft ab, die vom Parameter angegeben wird.  
  
## Syntax  
  
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
  
#### Parameter  
 `dwProperty`  
 Der Eigenschaftswert abzurufen.  
  
 `pvarIndex`  
 Wird nicht verwendet.  
  
 `pvarValue`  
 Der Wert der Eigenschaft.  
  
 Die Werte, die für `dwProperty` zulässig sind, werden in der folgenden Tabelle beschrieben.  
  
|Konstante|Wert|Bedeutung|  
|---------------|----------|---------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Erzwingt das Skriptmodul, um im Modus anstelle des Gleitkommamodus aufzuteilen.|  
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
 Der Host kann die SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTIONS\-Eigenschaft verwenden, um ein Skriptmodul mitzuteilen, dass keine anderen Skriptmodule vorhanden sein, um im globalen Objekt beizutragen.  Beispielsweise kann das Internet Explorer [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Modul darüber, dass die Seite, die gerendert wird, nur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skripts enthält.  Deshalb wird nur das [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Modul kann neue Eigenschaften zum globalen Objektfenster hinzufügen, und es gibt kein Modul der Visual Basic Scripting Edition \(VBScript\), das gleiche durchzuführen.  Das Modul kann dieses Flag ignorieren oder kann es verwenden, um die Verwaltung von neuen Member zu optimieren, die dem globalen Objekt hinzugefügt werden.  
  
 Der Host kann die SCRIPTPROP\_INVOKEVERSIONING\-Eigenschaft verwenden, um den von unterstützt werden Sprachfunktionen auszuwählen, wenn das [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul gestartet wird.  Wenn diese Eigenschaft auf 1 \(SCRIPTLANGUAGEVERSION\_5\_7\) festgelegt ist, sind die verfügbaren Sprachfunktionen identisch, die die, die in Version 5.7 des [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmoduls angezeigt.  Wenn es auf 2 \(SCRIPTLANGUAGEVERSION\_5\_8\) festgelegt ist, sind die verfügbaren Sprachfeatures, die in Version 5.7 zusätzlich zu den Funktionen angezeigt, die in Version 5.8 hinzugefügt wurden.  Diese Eigenschaft ist standardmäßig auf 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\) festgelegt, das der festgelegten Sprachfunktion entspricht, die in Version 5.7 ist, es sei denn, der Host ein anderes Standardverhalten unterstützt.  Beispielsweise entscheidet Internet Explorer 8 in die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Sprachfunktionen, die standardmäßig durch das [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Skriptmodul der Version 5.8 unterstützt werden, wenn der Dokumente für Internet Explorer 8 "Internet Explorer 8\-Standard" Modus ist.  
  
## Siehe auch  
 [Definieren von Dokumenten\-Kompatibilität](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Versionsinformationen](../../javascript/reference/javascript-version-information.md)