---
title: Ressourcenkonfliktansicht – Konfliktdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dddc9c85731137c6499e976b4b571396af297f7a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810350"
---
# <a name="resource-contentions-view---contention-data"></a>Ressourcenkonfliktansicht – Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Ansicht für Ressourcenkonflikte führt Ressourcenkonfliktdaten für die Ressourcen auf, die die Quelle der Konfliktereignisse waren. Ein Konfliktereignis tritt auf, wenn eine Funktion in einem Thread gezwungen wird, auf den Zugriff auf die Ressource zu warten, da eine Funktion in einem anderen Thread exklusiven Zugriff auf die Ressource abgerufen hat. Jede Ressource ist der Stammknoten einer Aufrufstruktur, die Ausführungspfade der Funktion anzeigt, die die Konfliktereignisse geführt haben.  
  
## <a name="data-values"></a>Datenwerte  
  
### <a name="resource-values"></a>Ressourcenwerte  
 Die Daten in eine Ressourcenzeile zeigen die Gesamtzeit an, in der der Zugriff auf die Ressource in Profilerstellungsdaten blockiert war und die Gesamtzahl von Konfliktereignissen, die aufgrund von Konflikten beim Dateizugriff auf diese Ressource aufgetreten sind. Inklusive und exklusive Werte für eine Ressource sind immer gleich.  
  
### <a name="function-values"></a>Funktionswerte  
 Funktionswerte basieren auf den Instanzen der Funktion, die in der im Ausführungspfad dargestellten Ausführungsstruktur aufgetreten sind.  
  
-   Exklusive Werte basieren auf den Ereignissen, die während der Ausführung von Anweisungen im Funktionsrumpf aufgetreten. Aufgetretene Ereignisse in Funktionen, die von der Funktion aufgerufen wurden, sind nicht in den exklusiven Werten enthalten.  
  
-   Inklusive Werte basieren auf den Ereignissen, die aufgetreten sind, als die Funktion ausgeführt wurde, oder eine Funktion, die von der Funktion aufgerufen wurde.  
  
### <a name="percentage-values"></a>Prozentsatzgröße  
 Prozentwerte basieren auf der Gesamtzeit oder den Konfliktereignissen in den Profilerstellungsdaten. Wenn der Bericht oder die Ansicht der Profilerstellung gefiltert wird, werden nur die blockierte Zeit und Konflikte in der gefilterten Daten als Gesamtwert verwendet.  
  
## <a name="navigating-the-resource-allocation-view"></a>Die Ansicht Ressourcenzuweisung navigieren  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name der Ressource oder der Funktion.|  
|**Exklusive blockierte Zeit %**|– Für eine Ressource, die gesamte Zeit, in der der Zugriff auf die Ressource blockiert wurde und ein Thread warten musste.<br />– Für eine Funktion, die Zeit, die diese Instanzen der Funktion für den Zugang auf die übergeordnete Ressource blockiert waren, während die Funktion Code im Funktionstext ausführte. Diese umfasst nicht den Zeitaufwand für Funktionen, die von dieser Funktion aufgerufen wurden.|  
|**Exklusive blockierte Zeit %**|– Für eine Ressource, der Prozentsatz der gesamten blockierten Zeit in den Profilerstellungsdaten, die für diese Ressource blockiert war<br />– Für eine Funktion, der Prozentsatz der gesamten blockierten Zeit in den Profilerstellungsdaten, die exklusiv für diese Funktionsinstanzen blockiert war|  
|**Exklusive Konflikte**|– Für eine Ressource, die Gesamtzahl der Fälle, in denen der Zugriff auf die Ressource blockiert war und einen Thread warten musste.<br />– Für eine Funktion, die Anzahl der Fälle, in denen der Zugriff diese Instanzen der Funktion auf die übergeordnete Ressource blockiert war, während die Funktion Code im Funktionstext ausführte. Dies umfasst nicht die blockierten Ereignisse für Funktionen, die von dieser Funktion aufgerufen wurden.|  
|**Exklusive Konflikte %**|– Für eine Ressource, der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die für den Zugriff auf diese Ressource Konfliktereignisse waren.<br />– Für eine Ressource, der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die für den Zugriff auf diese Funktionsinstanzen für die übergeordnete Ressource exklusive Konfliktereignisse waren.|  
|**Inklusive blockierte Zeit**|– Für eine Ressource, die gesamte Zeit, in der der Zugriff auf die Ressource blockiert wurde und ein Thread warten musste.<br />– Für eine Funktion, die Zeit, in der der Zugang dieser Instanzen der Funktion oder jede Funktion, die von den Instanzen aufgerufen wurde, auf die übergeordnete Ressource blockiert wurde, als die Funktion Code im Funktionstext ausführte.|  
|**Inklusive blockierte Zeit %**|– Für eine Ressource, der Prozentsatz der gesamten blockierten Zeit in den Profilerstellungsdaten, die für diese Ressource blockiert war<br />– Für eine Ressource, der Prozentsatz der gesamten blockierten Zeit in der Profilerstellung, die für die Instanzen dieser Funktion blockiert wurde.|  
|**Inklusive Konflikte %**|– Für eine Ressource, die Gesamtzahl der Fälle, in denen der Zugriff auf die Ressource blockiert war und einen Thread warten musste.<br />– Für eine Funktion, der Prozentsatz aller Konfliktereignisse in der Profilerstellung, die für den Zugriff auf die Instanzen der Funktion für die übergeordnete Ressource inklusive Konfliktereignisse waren.|  
|**Inklusive Konflikte %**|– Für eine Ressource, der Prozentsatz aller Konfliktereignisse in der Profilerstellung, die für den Zugriff auf diese Ressource Konfliktereignisse waren.<br />– Für eine Funktion, die Anzahl der Fälle, in denen der Zugriff dieser Instanzen der Funktion auf die übergeordnete Ressource blockiert war, während die Funktion Code im Funktionstext ausführte. Dies umfasst nicht die blockierten Ereignisse für Funktionen, die von dieser Funktion aufgerufen wurden.|  
|**Ebene**|Die Tiefe dieser Funktion in der Aufrufstruktur. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess-ID**|Der Prozess-ID (PID) des Prozesses, in dem die Funktion ausgeführt wurde.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|



