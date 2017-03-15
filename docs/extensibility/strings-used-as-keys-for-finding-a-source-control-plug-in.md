---
title: "Zeichenfolgen, die als Schl&#252;ssel f&#252;r ein Quellcodeverwaltungs-Plug-in zu suchen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins zum Suchen von Zeichenfolgen"
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Zeichenfolgen, die als Schl&#252;ssel f&#252;r ein Quellcodeverwaltungs-Plug-in zu suchen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden Zeichenfolgen sind die Schlüssel für den Zugriff auf die Registrierung, um Informationen zu den Datenquellen\-Steuerelement\-Plug\-in finden.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, und `STR_SCCPROVIDERNAME` Registry\-Schlüssel oder Werte verwendet, um eine DLL\-Datei als ein Quellcodeverwaltungs\-Plug\-In für Visual Studio zu registrieren.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, und `SCC_STATUS_FILE` werden verwendet, um das Format der MSSCCPRJ beschreiben. SCC\-Datei.  
  
## Zeichenfolgenschlüssel und Werte  
  
|Taste|Wert|  
|-----------|----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Quellcode|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC\_Project\_Name|  
|`SCC_PROJECTAUX_KEY`|SCC\_Aux\_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|Eine Quellcodedatei\-Steuerelement|  
|`SCC_NSE`|Namespace\-Erweiterung|  
|`SCC_NSE_PREFIX`|Präfix\-Protokolls|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|Helpcollection hinzu|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\\Microsoft\\SourceSafe|  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [Gewusst wie: Installieren Sie ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ. SCC\-Datei](../extensibility/mssccprj-scc-file.md)