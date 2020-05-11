---
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718903"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Stellt einen Symbolanbieter dar, der direkten Zugriff auf Metadaten und Kernsymbolschnittstellen hat.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Ruft den Anwendungsdomänenbezeichner mit der Debugadresse ab.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Ruft Informationen zu den Modulen in der Symbolgruppe ab.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Ruft Informationen über die Symbolgruppe ab, der der Symbolanbieter angehört.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Ruft die Metadatenimportinformationen ab.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Ruft Informationen über die Methode an der angegebenen Debugadresse ab.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Ruft einen Symbolleser für nicht verwalteten Code ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle kann anstelle der meisten anderen Symbolanbieterschnittstellen verwendet werden. Es bietet direkten Zugriff `CorSym` auf die Metadaten und Schnittstellen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
