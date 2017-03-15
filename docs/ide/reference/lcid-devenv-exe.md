---
title: "/LCID (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/l (Devenv-Schalter)"
  - "/lcid (Devenv-Schalter)"
  - "Devenv, /LCID-Schalter"
  - "Standardsprache"
  - "LCID (Devenv-Schalter)"
  - "Gebietsschema-IDs"
  - "Gebietsschema-IDs, Einstellung für IDE"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt die Standardsprache fest, die in der integrierten Entwicklungsumgebung \(IDE\) für Text, Währung und andere Werte verwendet wird.  
  
## Syntax  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## Argumente  
 `LocaleID`  
 Erforderlich.  Die LCID \(Lokale ID\) der angegebenen Sprache.  
  
## Hinweise  
 Die IDE wird geöffnet und die standardmäßige natürliche Sprache für die Umgebung geladen.  Diese Änderung bleibt über die Sitzung hinaus erhalten und wird im Dialogfeld **Optionen** unter **Umgebung** im Bereich **Internationale Einstellungen** in der IDE angezeigt.  
  
 Wenn die angegebene Sprache auf dem System des Benutzers nicht verfügbar ist, wird der \/LCID\-Schalter ignoriert.  
  
 In der folgenden Tabelle werden die LCIDs der von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützten Sprachen aufgelistet.  
  
|Sprache|LCID|  
|-------------|----------|  
|Chinesisch \(vereinfacht\)|2052|  
|Chinesisch \(traditionell\)|1028|  
|Englisch|1033|  
|Französisch|1036|  
|Deutsch|1031|  
|Italienisch|1040|  
|Japanisch|1041|  
|Koreanisch|1042|  
|Spanisch|3082|  
  
## Beispiel  
 In diesem Beispiel wird die IDE mit englischen Ressourcenzeichenfolgen geladen.  
  
```  
devenv /LCID 1033  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [Internationale Einstellungen, Umgebung, Dialogfeld "Optionen"](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)