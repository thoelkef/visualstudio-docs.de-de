---
title: "Problembehandlung bei Office-Projektmappensicherheit"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Sicherheit [Office-Entwicklung in Visual Studio], Problembehandlung"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Problembehandlung bei Office-Projektmappensicherheit
  Dieses Thema enthält Tipps zur Lösung allgemeiner Probleme, die beim Sichern von Office\-Projektmappen auftreten können.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Vertrauenswürdige Projektmappen können nicht von eingeschränkten Sites installiert werden  
 Benutzer können eine Projektmappe von einem Webstandort installieren, wenn die Website in Internet Explorer in der eingeschränkten Sites aufgelistet ist.  Dies gilt auch, wenn die Projektmappe mit einem vertrauenswürdigen Zertifikat signiert wird.  
  
 Die URL des Bereitstellungsmanifests kann in eine von fünf Zonen kategorisiert werden:  
  
-   Arbeitsplatz  
  
-   Internet  
  
-   Lokales Intranet  
  
-   Vertrauenswürdige Sites  
  
-   Eingeschränkte Sites  
  
 Wenn der Speicherort des Bereitstellungsmanifests der Zone für eingeschränkte Websites zugeordnet wurde, wird die Projektmappe nicht von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installiert.  Ist der Speicherort bekannt und gilt er als vertrauenswürdig, kann der Benutzer den Speicherort aus der Zone der eingeschränkten Sites entfernen und die Projektmappe installieren.  Weitere Informationen zum Verwalten von Zonen finden Sie unter [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Projektmappen können nicht von Netzwerkfreigaben oder Webadressen aus installiert werden, wenn die verstärkte Sicherheitskonfiguration für Internet Explorer 7 installiert ist  
 Die verstärkte Sicherheitskonfiguration für Internet Explorer \(IEESC\) in Windows Server 2003 und höher und Internet Explorer 7 und höher, schränkt die Fähigkeit von Benutzern beträchtlich ein, das Internet zu durchsuchen.  Wenn Benutzer versuchen, Office\-Projektmappen von einer Netzwerkfreigabe oder Webadresse aus zu installieren, wird möglicherweise die folgende Fehlermeldung: "Benutzerdefinierte Funktionen können in dieser Anwendung kann nicht auf, weil das Zertifikat, das verwendet wird, um das Bereitstellungsmanifest für *Projektmappenname* zu signieren, nicht vertrauenswürdig ist.  Wenden Sie sich an den Administrator, um weitere Unterstützung zu erhalten."  
  
 von IEESC und Internet Explorer 7 und höher, die URL des Bereitstellungsmanifests in der Internetzone kategorisiert ist, muss das Manifest ein Zertifikat von einer vertrauenswürdigen Herausgebers haben, oder kann die Projektmappe nicht installiert werden.  Wenn IEESC nicht verwendet wird, gilt als Standardverhalten, dass der Endbenutzer aufgefordert wird, eine Entscheidung über die Vertrauenswürdigkeit zu treffen.  
  
 Um die Wirkung von IEESC und Internet Explorer 7 zu verwalten und höher, identifizieren Sie die Websites und Pfade \(Universal Naming Convention\) denen Sie ihnen einer der vertrauenswürdigen Sicherheitszonen und hinzufügen \(Lokales Intranet oder Vertrauenswürdige Sites\). Informationen darüber, wie Zonen, finden Sie unter [Konfigurieren von vertrauenswürdigen Herausgebern ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  