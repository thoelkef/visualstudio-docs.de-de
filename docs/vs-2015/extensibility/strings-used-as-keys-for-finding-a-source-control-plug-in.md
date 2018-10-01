---
title: Zeichenfolgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-in verwendet werden. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e2a663f11834a063faa0017cd37f6f542ab98ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514477"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Zeichenfolgen, die als Schlüssel für die Suche nach einer Datenquellen-Steuerelement-Plug-Ins](https://docs.microsoft.com/visualstudio/extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in).  
  
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
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|  
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

