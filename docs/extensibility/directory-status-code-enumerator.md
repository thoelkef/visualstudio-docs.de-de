---
title: Verzeichnisstatuscode-Enumerator | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e62685a1a351c9a5773e18a53316106a18af66a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694659"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnisstatuscode-enumerator
Die `SccDirStatus` Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses in das Quellcodeverwaltungssystem angeben. Diese Enumeration wird verwendet, durch die [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Dies wurde in Version 1.2 von die Source-Plug-in-API eingeführt.

## <a name="syntax"></a>Syntax

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Member
 SCC_DIRSTATUS_INVALID-Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.

 SCC_DIRSTATUS_NOTCONTROLLED-Verzeichnis ist nicht unter quellcodeverwaltung.

 SCC_DIRSTATUS_CONTROLLED Verzeichnis befindet sich unter quellcodeverwaltung.

 SCC_DIRSTATUS_EMPTYPROJ-Projekt für dieses Verzeichnis ist leer.

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)