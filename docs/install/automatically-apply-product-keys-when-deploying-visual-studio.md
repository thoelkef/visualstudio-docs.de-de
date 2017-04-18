---
title: "Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 36a774583f5125ecc09210c9ad5da15ec800f870
ms.lasthandoff: 04/03/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio
Sie können den Product Key programmgesteuert als Teil eines Skripts anwenden, das zum Automatisieren der Bereitstellung von Visual Studio verwendet wird. Product Keys können während der Installation von Visual Studio oder nach der abgeschlossenen Installation auf einem Gerät programmgesteuert festgelegt werden.  

## <a name="apply-the-license-during-installation"></a>Anwenden der Lizenz während der Installation  
 Verwenden Sie den `--productKey`-Parameter, um einen Product Key beim Setupvorgang von Visual Studio anzuwenden. Dieser Setupparameter kann mit dem `--quiet parameter`-Parameter verwendet werden, um Visual Studio in einem bereits lizenzierten Status für den Endbenutzer zu installieren. Öffnen Sie zum Verwenden des `--productKey`-Parameters eine Eingabeaufforderung. Führen Sie das Setupprogramm (z.B. „vs_enterprise.exe“ oder „vs_professional.exe“) aus, und legen Sie den `--productKey`-Parameter mit einem Product Key (25 Zeichen) mit oder ohne Bindestriche fest:  

 Dies ist eine Beispielbefehl für die Installation von Visual Studio 2015 Enterprise mit Product Key AAAAABBBBBCCCCCDDDDDEEEEEEE:  

 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  

## <a name="apply-the-license-after-installation"></a>Anwenden der Lizenz nach der Installation  
 Sie können eine installierte Version von Visual Studio mit einem Product Key aktivieren, indem Sie das Hilfsprogramm „storePID.exe“ auf den Zielcomputern im automatischen Modus verwenden. „StorePID.exe“ ist ein Hilfsprogramm, das mit Visual Studio **\<Laufwerk>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe** installiert wird.  

 Führen Sie das Hilfsprogramm „storePID.exe“ mit erhöhten Rechten aus, indem Sie entweder einen System Center-Agent oder eine Eingabeaufforderung mit erhöhten Rechten gefolgt vom Product Key (einschließlich der Bindestriche) und dem Microsoft Product Code (MPC) verwenden. Schließen Sie unbedingt die Bindestriche in den Product Key mit ein.  

 `StorePID.exe [product key including the dashes] [MPC]`  

 Dies ist eine Beispielbefehlszeile für die Installation von Visual Studio 2017 Enterprise mit einem MPC von 08860 und dem Product Key „AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE“:  

 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  

 In der folgenden Tabelle werden die MPC-Codes für jede Edition von Visual Studio aufgelistet:  

|Visual Studio-Edition | MPC |  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866|
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  

Wenn der Product Key im Hilfsprogramm „StorePID.exe“ erfolgreich angewendet wurde, wird 0 zurückgegeben. Wenn Fehler gefunden werden, wird eine Zahl zwischen 1 und 6 zurückgegeben.  

## <a name="see-also"></a>Siehe auch  
 * [Installieren von Visual Studio](../install/install-visual-studio.md)
 * [Erstellen einer Offlineinstallation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)

