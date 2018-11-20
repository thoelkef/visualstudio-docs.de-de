---
title: 'Vorgehensweise: Beschränken der Instrumentierung auf bestimmte DLLs | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 054a281d445f5910e9a2d635bb453dd283425453
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803460"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Gewusst wie: Beschränken der Instrumentierung auf bestimmte DLLs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe der Instrumentierungs-Profilerstellungsmethode können Sie die Auflistung von Profilerstellungsdaten auf eine oder mehrere DLLs in einer Anwendung beschränken. Erstellen Sie eine Leistungssitzung, die die DLL-Datei als Ziel enthält, um das Profil von einer oder mehreren DLLs in einer Anwendung zu erstellen. Sie können die DLLS, für die Sie ein Profil erstellen möchten, als Projekt in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe oder als unabhängige Binärdateien angeben.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>So beschränken Sie die Instrumentation auf bestimme DLLS in einer Visual Studio-Projektmappe  
  
1.  Öffnen Sie die Projektmappe, die die DLL enthält, in [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Klicken Sie im Menü **Analysieren** auf **Leistungs-Assistenten starten**.  
  
3.  Wählen Sie **Instrumentation** als Profilerstellungsmethode aus, und klicken Sie anschließend auf **Weiter**.  
  
4.  Wählen Sie aus **Für welches der folgenden verfügbaren Ziele möchten Sie ein Profil erstellen?** den Namen des DLL-Projekts aus, und klicken Sie anschließend auf **Weiter**.  
  
5.  Klicken Sie auf **Fertig stellen**, um den Assistenten zu beenden und um im Fenster **Leistungs-Explorer** die neue Leistungssitzung anzuzeigen.  
  
6.  Klicken Sie mit der rechten Maustaste auf **Ziele**, und wählen Sie **Zielprojekt hinzufügen** aus.  
  
7.  Wählen Sie aus der Liste **Zielprojekt hinzufügen** das ausführbare Projekt aus, das Sie zum Ausführen der DLL verwenden möchten.  
  
     Dies ist optional. Sie können alle DLL-Projekte hinzufügen, für die Sie ein Profil erstellen möchten.  
  
8.  Klicken Sie mit der rechten Maustaste auf den Projektnamen, und deaktivieren Sie das Kontrollkästchen **Instrumentieren**, um die Datensammlung für ein zusätzliches Projekt zu verhindern.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>So geben Sie bestimmte DLLs als unabhängige Binärdateien zur Profilerstellung an  
  
1.  Öffnen Sie [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Klicken Sie im Menü **Analysieren** auf **Leistungs-Assistenten starten**.  
  
3.  Wählen Sie aus **Für welches der folgenden verfügbaren Ziele möchten Sie ein Profil erstellen?** **Profil einer Dynamic Link Library (.DLL) erstellen** aus und klicken Sie anschließend auf **Weiter**.  
  
4.  Führen Sie auf der zweiten Seite des Assistenten die folgenden Schritte aus:  
  
    -   Geben Sie den Pfad und den Namen der DLL-Datei an, deren Profil Sie im **DLL-Pfad** erstellen möchten. Sie können auch auf die Schaltfläche mit den Auslassungspunkten (...) klicken, um die Datei im Dialogfeld **Dynamic Link Library, für die ein Profil erstellt werden soll** zu suchen. Beachten Sie, dass Sie die Kopie der DLL-Datei angeben müssen, die durch die ausführbare Datei (.exe) gestartet wird, die Sie als Nächstes auswählen.  
  
    -   Geben Sie im **Pfad der ausführbaren Datei** den Pfad und den Namen der ausführbaren Datei (.exe) an, die in der DLL-Datei ausgeführt wird. Sie können auch auf die Schaltfläche mit den Auslassungspunkten (...) klicken, um die Datei im Dialogfeld **Zu startende ausführbare Datei** zu suchen.  
  
    -   Dies ist optional. Geben Sie in **Befehlszeilenargumente** Befehlszeilenargumente an, die an die ausführbare Datei übergeben werden sollen. Geben Sie ggf. in **Arbeitsverzeichnis** das Arbeitsverzeichnis für die Anwendung an.  
  
    -   Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie **Instrumentation** als Profilerstellungsmethode aus, und klicken Sie anschließend auf **Weiter**.  
  
6.  Klicken Sie auf **Fertig stellen**, um den Assistenten zu beenden und um im Fenster **Leistungs-Explorer** die neue Leistungssitzung anzuzeigen.  
  
7.  Dies ist optional. Klicken Sie mit der rechten Maustaste auf **Ziele** und wählen Sie anschließend **Zielbinärdatei hinzufügen** aus, um weitere DLL-Dateien hinzuzufügen. Wählen Sie die Dateien vom Dialogfeld **Zielbinärdateien hinzufügen** aus.  
  
    > [!NOTE]
    >  Geben Sie nicht die ausführbare Datei (.exe) an, die die DLLs ausführt.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Vorgehensweise: Beschränken der Instrumentierung auf bestimmte Funktionen](../profiling/how-to-limit-instrumentation-to-specific-functions.md)



