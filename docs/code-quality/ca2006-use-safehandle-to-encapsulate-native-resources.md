---
title: "CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|Kategorie \(Category\)|Microsoft.Reliability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 In verwaltetem Code wird <xref:System.IntPtr> für den Zugriff auf systemeigene Ressourcen verwendet.  
  
## Regelbeschreibung  
 Die Verwendung von `IntPtr` in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen.  Alle Vorkommen von `IntPtr` müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von <xref:System.Runtime.InteropServices.SafeHandle> \(oder einer ähnlichen Technologie\) erforderlich ist.  Probleme treten auf, wenn `IntPtr` eine systemeigene Ressource darstellt \(Speicher, Dateihandle oder Socket\), von der angenommen wird, dass sie sich im Besitz des verwalteten Codes befindet.  Wenn verwalteter Code die Ressource besitzt, muss er auch die systemeigenen, ihm zugeordneten Ressourcen freigeben, da andernfalls damit Ressourcenverluste verursacht würden.  
  
 In solchen Szenarien treten ebenfalls Sicherheitsrisiken oder Zuverlässigkeitsprobleme auf, wenn Multithreaded\-Zugriff auf `IntPtr` zulässig ist und zum Freigeben der durch `IntPtr` dargestellten Ressource bereitgestellt wird.  Diese Probleme beinhalten die Wiederverwendung des `IntPtr`\-Werts bei einer Ressourcenfreigabe, während die Ressource gleichzeitig in einem anderen Thread verwendet wird.  Dies kann Racebedingungen verursachen, bei denen ein Thread Daten lesen oder schreiben kann, die einer falschen Ressource zugeordnet sind.  Wenn der Typ beispielsweise ein Betriebssystemhandle als `IntPtr` speichert und zulässt, dass Benutzer sowohl die **Close**\-Methode als auch eine beliebige andere Methode aufrufen und dieses Handle \(ohne Synchronisierung\) gleichzeitig verwenden, hat der Code ein Problem beim Recyceln von Handles.  
  
 Dieses Handlerecyclingproblem kann zu Datenbeschädigung und häufig Sicherheitslücken führen.  `SafeHandle` und seine nebengeordnete Klasse <xref:System.Runtime.InteropServices.CriticalHandle> stellen einen Mechanismus bereit zum Kapseln eines systemeigenen Handles für eine Ressource, damit solche Threadingprobleme vermieden werden können.  Zudem können Sie `SafeHandle` und `CriticalHandle` für andere Threadingprobleme verwenden, beispielsweise für die sorgfältige Kontrolle der Lebensdauer von verwalteten Objekten, die eine Kopie des systemeigenen Handles über Aufrufe an systemeigene Methoden enthalten,  d. h., Sie können Aufrufe an `GC.KeepAlive` häufig entfernen.  Der zusätzliche Leistungsaufwand, der durch die Verwendung von `SafeHandle` und, in geringerem Maße, die Verwendung von `CriticalHandle` entsteht, kann häufig durch einen sorgfältigen Entwurf reduziert werden.  
  
## Behandeln von Verstößen  
 Konvertieren Sie `IntPtr` in `SafeHandle`, um den Zugriff auf systemeigene Ressourcen sicher zu verwalten.  Im <xref:System.Runtime.InteropServices.SafeHandle>\-Referenzthema finden Sie Beispiele.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Warnung sollte nicht unterdrückt werden.  
  
## Siehe auch  
 <xref:System.IDisposable>