---
title: Idebugsymbolproviderdirect | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ad768419786f78277b791997538785265a24c0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153100"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Stellt einen Symbol Anbieter dar, der direkten Zugriff auf Metadaten und Kern Symbol Schnittstellen hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Ruft den Anwendungs Domänen Bezeichner anhand der debugadresse ab.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Ruft Informationen zu den Modulen in der Symbolgruppe ab.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Ruft Informationen über die Symbolgruppe ab, in der der Symbol Anbieter ein Member ist.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Ruft die Informationen zum Metadatenimport ab.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Ruft Informationen zur Methode an der angegebenen debugadresse ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Ruft einen Symbol Reader für nicht verwalteten Code ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle kann anstelle der meisten anderen Symbol Anbieter Schnittstellen verwendet werden. Er bietet direkten Zugriff auf die Metadaten und `CorSym` Schnittstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
