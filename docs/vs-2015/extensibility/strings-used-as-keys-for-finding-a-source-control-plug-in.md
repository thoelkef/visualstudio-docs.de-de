---
title: Zeichenfolgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-in verwendet werden. | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83ba843e318aac6a74d318978e42e2f81802d8ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160577"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die nachfolgenden Zeichenfolgen sind die Schlüssel für den Zugriff auf die Registrierung, um Informationen über das Quellcodeverwaltungs-Plug-in finden.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, und `STR_SCCPROVIDERNAME` sind Registrierungsschlüssel bzw.-Werte verwendet, um eine DLL als ein Quellcodeverwaltungs-Plug-In für Visual Studio zu registrieren.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, und `SCC_STATUS_FILE` verwendet, um das Format der MSSCCPRJ beschreiben. SCC-Datei.  
  
## <a name="string-keys-and-values"></a>Zeichenfolgenschlüsseln und Werten  
  
|Key|Wert|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Quellcodeverwaltung|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|Eine Quellcodedatei-Steuerelement|  
|`SCC_NSE`|Namespace-Erweiterung|  
|`SCC_NSE_PREFIX`|Protokoll-Präfix|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|Helpcollection hinzu|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)
