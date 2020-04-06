---
title: Zeichenfolgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendet werden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699715"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen
Die folgenden Zeichenfolgen sind die Schlüssel für den Zugriff auf die Registrierung, um Informationen zum Quellcodeverwaltungs-Plug-In zu finden.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`, `STR_SCCPROVIDERNAME` und sind Registrierungsschlüssel oder -werte, die zum Registrieren einer DLL als Quellcodeverwaltungs-Plug-In für Visual Studio verwendet werden.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` und werden verwendet, um das Format des MSSCCPRJ zu beschreiben. SCC-Datei.

## <a name="string-keys-and-values"></a>Zeichenfolgenschlüssel und -werte

|Schlüssel|Wert|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software-SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Quellcodeverwaltung|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Eine Quellcodeverwaltungsdatei|
|`SCC_NSE`|Namespace-Erweiterung|
|`SCC_NSE_PREFIX`|Protokalpräfix|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software- und Software-Microsoft-SourceSafe|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)
