---
title: Zeichen folgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-ins verwendet werden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07962ff9e0f9371b1fc308a35600a6819602b4f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719450"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen
Die folgenden Zeichen folgen sind die Schlüssel für den Zugriff auf die Registrierung, um Informationen über das Quellcodeverwaltungs-Plug-in zu suchen.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH` und `STR_SCCPROVIDERNAME` sind Registrierungsschlüssel oder-Werte, die zum Registrieren einer DLL als Quellcodeverwaltungs-Plug-in für Visual Studio verwendet werden.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE` und `SCC_STATUS_FILE` werden verwendet, um das Format von Mssccprj zu beschreiben. SCC-Datei.

## <a name="string-keys-and-values"></a>Zeichen folgen Schlüssel und-Werte

|Key|Wert|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\sourcecodecontrolprovider|
|`STR_PROVIDERREGKEY`|Providerregkey|
|`STR_SCCPROVIDERPATH`|Sccserverpath|
|`STR_SCCPROVIDERNAME`|Sccservername|
|`STR_SCC_INI_SECTION`|Quell Code Verwaltung|
|`STR_SCC_INI_KEY`|Sourcecodecontrolprovider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|Mssccprj. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Eine Quell Code Verwaltungs Datei|
|`SCC_NSE`|Namespace Erweiterung|
|`SCC_NSE_PREFIX`|Protopräfix|
|`SCC_NSE_DisableOpenSCC`|Disableopenfromsourcecontrol|
|`STR_SCCHELPCOLLECTION`|Helpcollection|
|`STR_UI_LANGUAGE`|Eigenschaft UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\microsoft\sourcesafe|

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)