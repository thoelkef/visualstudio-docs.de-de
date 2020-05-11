---
title: Dateistatuscode-Enumerator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711452"
---
# <a name="file-status-code-enumerator"></a>Dateistatuscode-Enumerator
Der `SccStatus` Enumerator enthält benannte Konstantewerte, die den Status einer Datei im Quellcodeverwaltungssystem angeben. Diese Enumeration wird von Der [SccQueryInfo](../extensibility/sccqueryinfo-function.md) und der `POPLISTFUNC` Rückruffunktion verwendet (Details finden Sie unter [POPLISTFUNC).](../extensibility/poplistfunc.md)

## <a name="syntax"></a>Syntax

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Member
 SCC_STATUS_INVALID Status konnte nicht abgerufen werden; sich nicht darauf verlassen.

 SCC_STATUS_NOTCONTROLLED Datei wird nicht unter Quellcodeverwaltung.

 SCC_STATUS_CONTROLLED Datei wird unter Quellcodeverwaltung.

 SCC_STATUS_CHECKEDOUT ausgecheckt vom aktuellen Benutzer auf dem lokalen Datenträger.

 SCC_STATUS_OUTOTHER Datei wird von einem anderen Benutzer ausgecheckt.

 SCC_STATUS_OUTEXCLUSIVE Datei wird exklusiv ausgecheckt.

 SCC_STATUS_OUTMULTIPLE Datei wird von mehr als einem Benutzer ausgecheckt.

 SCC_STATUS_OUTOFDATE Die Datei ist nicht die neueste.

 SCC_STATUS_DELETED Datei wurde aus dem Projekt gelöscht.

 SCC_STATUS_LOCKED Datei ist gesperrt; keine weiteren Versionen zulässig.

 SCC_STATUS_MERGED Datei wurde zusammengeführt, aber noch nicht fixiert/verifiziert.

 SCC_STATUS_SHARED Datei wird von Projekten gemeinsam genutzt.

 SCC_STATUS_PINNED Datei wird für eine explizite Version freigegeben.

 SCC_STATUS_MODIFIED Datei wurde geändert/beschädigt/verletzt.

 SCC_STATUS_OUTBYUSER Datei wird vom aktuellen Benutzer ausgecheckt.

 SCC_STATUS_NOMERGE Datei kann nie mit einem GET zusammengeführt werden und muss nicht gespeichert werden.

 SCC_STATUS_RESERVED_1 für den internen Gebrauch reserviert.

 SCC_STATUS_RESERVED_2 reserviert für den internen Gebrauch.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
