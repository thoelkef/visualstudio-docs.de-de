---
title: Verzeichnisstatuscode-Enumerator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712157"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnisstatuscode-Enumerator
Der `SccDirStatus` Enumerator enthält benannte Konstantewerte, die den Status eines Verzeichnisses im Quellcodeverwaltungssystem angeben. Diese Enumeration wird von Der [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)verwendet. Dies wurde in Version 1.2 der Quellcodeverwaltungs-Plug-In-API eingeführt.

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
 SCC_DIRSTATUS_INVALID Status konnte nicht abgerufen werden; sich nicht darauf verlassen.

 SCC_DIRSTATUS_NOTCONTROLLED Verzeichnis wird nicht unter Quellcodeverwaltung.

 SCC_DIRSTATUS_CONTROLLED Verzeichnis befindet sich unter Quellcodeverwaltung.

 SCC_DIRSTATUS_EMPTYPROJ diesem Verzeichnis entsprechenden Projekt ist leer.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
