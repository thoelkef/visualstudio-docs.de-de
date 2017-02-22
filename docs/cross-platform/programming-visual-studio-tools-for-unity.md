---
title: "Programmieren mit Visual Studio-Tools f&#252;r Unity | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "crdun"
manager: "crdun"
---
# Programmieren mit Visual Studio-Tools f&#252;r Unity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt finden Sie Beispiele für die Verwendung der Visual Studio\-Tools für Unity\-API.  
  
## Beispiele  
 Hier sind einige Beispiele, die zeigen, wie Sie Visual Studio\-Tools für Unity\-APIs verwenden können.  
  
### Anpassen von mit VSTU erstellten Projektdateien  
 Visual Studio\-Tools für Unity bieten während der Generierung der Projektdatei einen Rückruf im Unity\-Stil.  Informationen dazu, wie Sie die Projektdatei ändern können, immer wenn sie erneut generiert wird, finden Sie unter [Beispiel: Erstellung der Projektdatei](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### Freigeben des Unity\-Protokollrückrufs für VSTU  
 Visual Studio\-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann.  Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU\-Rückruf Ihren Rückruf stören.  Informationen dazu, wie Sie den Unity\-Protokollrückruf für VSTU freigeben können, finden Sie unter [Beispiel: Protokollrückruf](../cross-platform/share-the-unity-log-callback-with-vstu.md).