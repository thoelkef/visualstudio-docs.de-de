---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
Fügt den Namen eines Elements auf Stammebene den Namespace des Skripterstellungs\-Moduls hinzu.  Ein *Element auf der Stammebene* ist ein Objekt, das Eigenschaften und Methoden enthalten können und das eine Ereignisquelle auch enthalten kann.  
  
## Syntax  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### Parameter  
 `pszName`  
 \[in\] Der Name des Elements, wie im Skript angezeigt.  Der Name muss eindeutig sein und bleiben.  
  
 `dwFlags`  
 \[in\] Die Flags, die dem benannten Element zugeordnet sind.  Kann eine Kombination der folgenden Werte:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|Gibt an, dass der Name des Elements im Namespace des Skripts verfügbar ist.  Dies ermöglicht den Zugriff auf den Eigenschaften, Methoden und Ereignisse Elements.<br /><br /> Standardmäßig enthalten die Eigenschaften des Elements die Member des untergeordneten Elements.  Deshalb sind alle untergeordneten Objekteigenschaften und \-methoden \(und ihre untergeordneten Member, rekursiv\) zugänglich.|  
|SCRIPTITEM\_ISSOURCE|0x00000004|Gibt die Ereignisse des Elementquell an, die das Skript Skriptereignishandler haben kann.|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|Gibt an, dass das Element eine Auflistung globale Eigenschaften und Methoden ist, die dem Skript zugeordnet sind.  Seine Member werden als globale Variablen und Methoden erstellt.|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|Gibt an, dass das Element gespeichert werden soll, wenn das Skripterstellungsmodul gespeichert wird.|  
|SCRIPTITEM\_CODEONLY|0x00000200|Gibt an, dass das genannte Element ein nur für Code Objekt darstellt, und enthält keinen Member, zu erstellen.|  
|SCRIPTITEM\_NOCODE|0x00000400|Gibt an, dass das genannte Element nur ein Name, der hinzugefügt wird, und es besteht kein zu erstellen.|  
  
 `pdisp`  
 \[in\] `IDispatch``NamedItem` des Objekts, das verwendet wird, um Methoden, Eigenschaften oder die Ereignisquelle zu sammeln.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)