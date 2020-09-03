---
title: DEBUG_CUSTOM_VIEWER | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d10e0811044d7169eaf46f48f53389fa7b3076ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179168"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Eine-Struktur, die einen benutzerdefinierten Viewer oder eine typschnell Ansicht identifiziert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Member  
 dwID  
 Eine ID zur Unterscheidung mehrerer Viewer oder schnell Ansichten, die von einem solchen implementiert werden `GUID` .  
  
 bstraumenuname  
 Der Text, der im Dropdown Menü angezeigt wird.  
  
 bstrDescription  
 Eine Beschreibung des benutzerdefinierten Viewers oder der typschnell Ansicht (muss ein NULL-Wert sein, wenn er nicht verwendet wird).  
  
 guidlang  
 Sprache der Ausdrucks Auswertung für die Bereitstellung.  
  
 guidvendor  
 Hersteller der Bereitstellung der Ausdrucks Auswertung.  
  
 bstraumetric  
 Die Metrik, unter der der benutzerdefinierte Viewer oder die typschnell Ansicht `CLSID` gespeichert wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Liste dieser Struktur wird durch einen Aufrufen der [getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) -Methode zurückgegeben (und durch Erweiterung die [getcustomviewerlist](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) -Methode).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
