---
title: "Zeichenfolgen, die als Schlüssel für die Suche ein Quellcodeverwaltungs-Plug-in nach | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1acc753d2a02c3be88687a4e42d71d23e988af48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Zeichenfolgen, die als Schlüssel zum Suchen ein Quellcodeverwaltungs-Plug-in verwendet werden.
Die folgenden Zeichenfolgen sind die Schlüssel für den Zugriff auf die Registrierung, um Informationen zu den Datenquellen-Steuerelement-Plug-in finden.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, und `STR_SCCPROVIDERNAME` Registrierungsschlüssel oder Werte verwendet, um eine DLL-Datei als ein Quellcodeverwaltungs-Plug-In für Visual Studio zu registrieren.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, und `SCC_STATUS_FILE` werden verwendet, um das Format der MSSCCPRJ beschreiben. SCC-Datei.  
  
## <a name="string-keys-and-values"></a>Zeichenfolgeschlüssel und Werte  
  
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
|`SCC_NSE_PREFIX`|Präfix des Protokolls|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|Helpcollection hinzu|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Vorgehensweise: Installieren Sie ein Quellcodeverwaltungs-Plug-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)