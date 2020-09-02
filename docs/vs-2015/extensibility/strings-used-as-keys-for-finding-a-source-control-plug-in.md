---
title: Zeichen folgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-ins verwendet werden | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160577"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden Zeichen folgen sind die Schlüssel für den Zugriff auf die Registrierung, um Informationen über das Quellcodeverwaltungs-Plug-in zu suchen.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` und `STR_SCCPROVIDERNAME` sind Registrierungsschlüssel oder-Werte, die zum Registrieren einer DLL als Quellcodeverwaltungs-Plug-in für Visual Studio verwendet werden.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` und `SCC_STATUS_FILE` werden verwendet, um das Format von Mssccprj zu beschreiben. SCC-Datei.  
  
## <a name="string-keys-and-values"></a>Zeichen folgen Schlüssel und-Werte  
  
|Schlüssel|Wert|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\sourcecodecontrolprovider|  
|`STR_PROVIDERREGKEY`|Providerregkey|  
|`STR_SCCPROVIDERPATH`|Sccserverpath|  
|`STR_SCCPROVIDERNAME`|Sccservername|  
|`STR_SCC_INI_SECTION`|Quellcodeverwaltung|  
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
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\microsoft\sourcesafe|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-ins](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)
