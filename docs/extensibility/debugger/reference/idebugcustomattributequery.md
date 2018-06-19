---
title: IDebugCustomAttributeQuery | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef26d44f72f762749aff8758d68c7ee2fe765fc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105124"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Stellt eine Abfrage für benutzerdefinierte Attribute auf eine Methode oder generischen Typ dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Ruft ein benutzerdefiniertes Attribut mit dem angegebenen Namen ab.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Bestimmt, in der angegebenen benutzerdefinierten Attributs definiert ist.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll