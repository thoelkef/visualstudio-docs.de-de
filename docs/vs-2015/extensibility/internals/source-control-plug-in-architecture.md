---
title: Quellcodeverwaltungs-Plug-in-Architektur | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 370f88ce4d8fc372ce31e1e85e88d5379f4e1ba5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183377"
---
# <a name="source-control-plug-in-architecture"></a>Architektur von Quellcodeverwaltungs-Plug-Ins
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können der integrierten Entwicklungsumgebung (IDE) Unterstützung der Quell Code Verwaltung hinzufügen, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] indem Sie ein Quellcodeverwaltungs-Plug-in implementieren und anfügen. Die IDE stellt über die klar definierte Quellcodeverwaltungs-Plug-in-API eine Verbindung mit dem Quellcodeverwaltungs-Plug-in her. Die IDE stellt die Versions Kontroll Features des Quell Code Verwaltungssystems bereit, indem eine Benutzeroberfläche (UI) bereitgestellt wird, die aus Symbolleisten und Menübefehlen besteht. Das Quellcodeverwaltungs-Plug-in implementiert die Funktionen der Quell Code Verwaltung.  
  
## <a name="source-control-plug-in-resources"></a>Quellcodeverwaltungs-Plug-in-Ressourcen  
 Das Quellcodeverwaltungs-Plug-in stellt Ressourcen bereit, die Sie beim Erstellen und verbinden ihrer versionierungsanwendung mit der IDE unterstützen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Das Quellcodeverwaltungs-Plug-in enthält die API-Spezifikation, die von einem Quellcodeverwaltungs-Plug-in implementiert werden muss, damit es in die IDE integriert werden kann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Außerdem enthält Sie ein Codebeispiel (geschrieben in C++), das ein Skelett-Quellcodeverwaltungs-Plug-in zum Veranschaulichen der Implementierung wichtiger Funktionen implementiert, die mit der Quellcodeverwaltungs-Plug-in-API kompatibel sind.  
  
 Mit der API-Spezifikation für die Quellcodeverwaltungs-Plug-in können Sie jedes beliebige Quell Code Verwaltungssystem Ihrer Wahl nutzen, wenn Sie eine Quellcodeverwaltungs-dll mit den erforderlichen Funktionen erstellen, die in Übereinstimmung mit der Quellcodeverwaltungs-API implementiert sind.  
  
## <a name="components"></a>Komponenten  
 Das Quell Code Verwaltungs Adapter Paket im Diagramm ist die Komponente der IDE, die die Anforderung des Benutzers für einen Quell Code Verwaltungsvorgang in einen Funktions aufrut übersetzt, der vom Quellcodeverwaltungs-Plug-in unterstützt wird. Hierfür müssen die IDE und das Quellcodeverwaltungs-Plug-in ein effektives Dialogfeld aufweisen, das Informationen zwischen der IDE und dem Plug-in übermittelt. Damit dieses Dialogfeld durchgeführt werden kann, müssen beide die gleiche Sprache sprechen. Die in dieser Dokumentation beschriebene Quellcodeverwaltungs-Plug-in-API ist das gängige Vokabular für diesen Austausch.  
  
 ![Diagramm der Quellcode-Verwaltungsarchitektur](../../extensibility/internals/media/vs-sccsdk-plug-in-arch.gif "vs_sccsdk_plug_in_arch")  
Architektur Diagramm mit Interaktion zwischen vs und dem Quellcodeverwaltungs-Plug-in  
  
 Wie im Architektur Diagramm gezeigt, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hostet die Shell, die im Diagramm als vs-Shell gekennzeichnet ist, die Arbeitsprojekte des Benutzers und zugehörige Komponenten, z. b. die Editoren und die Projektmappen-Explorer. Das Quellcodeverwaltungs-Adapter Paket verarbeitet die Interaktion zwischen der IDE und dem Quellcodeverwaltungs-Plug-in. Das Quellcodeverwaltungs-Adapter Paket bietet eine eigene Benutzeroberfläche für die Quell Code Verwaltung. Dabei handelt es sich um die Benutzeroberfläche der obersten Ebene, mit der der Benutzer interagiert, um den Bereich eines Quell Code Verwaltungs Vorgangs zu initiieren und zu definieren.  
  
 Das Quellcodeverwaltungs-Plug-in kann über eine eigene Benutzeroberfläche verfügen, die aus zwei Teilen bestehen kann, wie in der Abbildung dargestellt. Das Feld mit der Bezeichnung "Vendor UI" stellt benutzerdefinierte Benutzeroberflächen Elemente dar, die Sie als Quellcodeverwaltungs-Plug-in-Ersteller bereitstellen. Diese werden direkt vom Quellcodeverwaltungs-Plug-in angezeigt, wenn der Benutzer einen erweiterten Quell Code Verwaltungsvorgang aufruft. Das Feld mit der Bezeichnung "Hilfsanwendung" ist ein Satz von Benutzeroberflächen Features für die Quellcodeverwaltungs-Plug-ins, die indirekt über die IDE aufgerufen werden. Das Quellcodeverwaltungs-Plug-in übergibt Benutzeroberflächen bezogene Nachrichten über spezielle Rückruf Funktionen, die von der IDE bereitgestellt werden, an die IDE. Die hilfsbenutzer Oberfläche ermöglicht eine nahtlose Integration in die IDE (häufig durch die Verwendung einer Schaltfläche " **erweitert** ") und bietet somit eine einheitlichere Benutzeroberfläche.  
  
 Ein Quellcodeverwaltungs-Plug-in kann Änderungen an der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Shell und folglich weder an das Quell Code Verwaltungs Adapter Paket noch an die Benutzeroberfläche der Quell Code Verwaltung durchführen, die von der IDE bereitgestellt wird. Es muss die Flexibilität, die durch die Implementierung der verschiedenen API-Funktionen für Quellcodeverwaltungs-Plug-ins geboten wird, optimal nutzen, die zu einer integrierten Obergrenze für den Endbenutzer beitragen. Der Referenz Abschnitt der Plug-in-API-Dokumentation der Quell Code Verwaltung enthält Informationen für einige erweiterte Funktionen für die Quellcodeverwaltungs-Plug-ins. Um diese Features auszunutzen, muss das Quellcodeverwaltungs-Plug-in während der Initialisierung seine erweiterten Funktionen für die IDE deklarieren und bestimmte erweiterte Funktionen für jede Funktion implementieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../../extensibility/source-control-plug-ins.md)   
 [Glossar](../../extensibility/source-control-plug-in-glossary.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
