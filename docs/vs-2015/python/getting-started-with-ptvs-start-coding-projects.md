---
title: 'Erste Schritte mit PTVS: Codieren beginnen (Projekte) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: a8e0bd339d8e7b6d145cc9a916dafc2be9fc975e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845783"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Erste Schritte mit PTVS: Codieren beginnen (Projekte)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe der Python-Tools für Visual Studio (PTVS) können Sie Ihren Code verwalten. 
 
 Sie können diese Anweisungen in einem sehr kurzen [Youtube-Video](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2) ansehen. 
 
 Wenn Sie Python bereits verwendet haben, wissen Sie, dass Ihr Projekt dadurch definiert wird, wie Sie Dateien auf dem Datenträger anordnen. Dies funktioniert hervorragend für einfache Python-Projekte, wenn Sie jedoch weitere Dateien (Webseiten mit JavaScript, Komponententests und Buildskripts) haben, können Dateisysteme zu Einschränkungen führen. Visual Studio verwendet Projekte, um drei Dinge zu erreichen. 
 
- Identifizieren Sie wichtige Dateien. Wichtige Dateien sind diejenigen, die Sie in ein Versionskontrollsystem einchecken (Quelldateien, Ressourcen usw.), nicht jedoch Dateien, die als Buildausgabe generiert werden. Wichtige Dateien sind auch solche, die Sie auf einen anderen Computer kopieren, damit eine andere Person in Ihrer App arbeiten kann. 
 
- Geben Sie an, wie Dateien verwendet werden sollen. Möglicherweise verfügen Sie über Dateien, die bei einer Dateiänderung von einem Tool verarbeitet werden müssen. Visual Studio-Projekte können diese Informationen aufzeichnen. 
 
- Definieren Sie die Grenzen Ihrer Komponenten. Wenn Sie über mehrere Komponenten in Ihrer App verfügen, können Sie jede in ein separates Projekt einfügen. Diese können schließlich auf verschiedenen Servern bereitgestellt, mit verschiedenen Build- oder Debugeinstellungen erstellt oder sogar in einer anderen von Visual Studio unterstützten Sprache geschrieben werden, wie beispielsweise C++ oder Node.js. 
 
  Es gibt mehrere Projektvorlagen, die Ihnen beim Einstieg helfen. Wenn Sie bereits über Python-Code verfügen, mit dem Sie arbeiten möchten, hilft der Assistent zum Erstellen von Projekten aus vorhandenen Codedateien dabei, ein Projekt zu erstellen, das all Ihre Dateien enthält. Für einige beliebte Frameworks sind mehrere Webprojekte vorhanden. Weitere Vorlagen stehen im Paket mit PTVS-Beispielen zur Verfügung. Es gibt Optionen, mit denen Sie dafür sorgen können, dass Webvorlagen mit anderen Frameworks funktionieren. Bei der Python-Anwendungsvorlage handelt es sich um ein leeres, sauberes Projekt. Es gibt ein Modul, um Ihnen den Einstieg zu erleichtern. 
 
  Visual Studio zeigt die geöffneten Projekte im Projektmappen-Explorer-Fenster, einschließlich aller Dateien, Suchpfade und Python-Umgebungen. Um neue Elemente hinzuzufügen, wählen Sie den Projektordner aus, und wählen Sie aus dem Kontextmenü (klicken Sie auf die Schaltfläche mit dem Zeiger nach rechts) die Optionen "Hinzufügen" und "Neues Element". Sie können ein beliebiges Element im Dialogfeld auswählen, den Namen des Elements anpassen und das Element zum Projekt hinzufügen. 
 
  Sie können Elemente per Drag & Drop in den Projektmappen-Explorer einfügen. Wenn Sie bereits Dateien in Ihre Projektverzeichnisstruktur kopiert haben, können Sie oben im Projektmappen-Explorer die Option "Alle Dateien anzeigen" auswählen. Anschließend können Sie die Elemente auswählen, die Sie hinzufügen möchten, und aus dem Kontextmenü die Option "In Projekt einschließen" auswählen. 
 
  Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2) ansehen. 
 
## <a name="see-also"></a>Siehe auch 
 [Wiki-Dokumentation](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS Videos – Einstieg und ausführliche Erläuterungen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

