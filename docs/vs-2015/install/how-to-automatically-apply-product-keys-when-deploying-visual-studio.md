---
title: 'Gewusst wie: Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 5b2a8bf9a6bd2644e91104ef9a4cd631c490feee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751381"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Vorgehensweise: Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [automatisch Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Sie können den Product Key programmgesteuert als Teil eines Skripts zum Automatisieren der Bereitstellung von Visual Studio 2015 verwendet anwenden. Product Keys können während der Installation von Visual Studio oder nach der abgeschlossenen Installation auf einem Gerät programmgesteuert festgelegt werden.  
  
## <a name="apply-the-license-during-installation"></a>Anwenden der Lizenz während der Installation  
 Verwenden Sie den/ProductKey-Parameter, um einen Product Key beim Setupvorgang von Visual Studio anzuwenden. Dieser Setupparameter kann mit dem /Silent-Parameter verwendet werden, um Visual Studio in einem bereits lizenzierten Status für den Endbenutzer zu installieren. Öffnen Sie zum Testen des "/ProductKey"-Parameters eine Eingabeaufforderung. Führen Sie das Setupprogramm ("vs_enterprise.exe" oder "vs_professional.exe") aus, und legen Sie den "/ProductKey"-Parameter mit einem Product Key (25 Zeichen) fest, der keine Bindestriche enthält:  
  
 Dies ist eine Beispielbefehl für die Installation von Visual Studio 2015 Enterprise mit Product Key AAAAABBBBBCCCCCDDDDDEEEEEEE:  
  
 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>Anwenden der Lizenz nach der Installation  
 Sie können eine installierte Version von Visual Studio mit einem Product Key aktivieren, indem Sie das Hilfsprogramm „storePID.exe“ auf den Zielcomputern im automatischen Modus verwenden. StorePID.exe ist ein Hilfsprogramm, das mit Visual Studio installiert  **\<Laufwerk >:\\\Programme Dateien (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.  
  
 Führen Sie das Hilfsprogramm „storePID.exe“ mit erhöhten Rechten aus, indem Sie entweder einen System Center-Agent oder eine Eingabeaufforderung mit erhöhten Rechten gefolgt vom Product Key (einschließlich der Bindestriche) und dem Microsoft Product Code (MPC) verwenden. Schließen Sie unbedingt die Bindestriche in den Product Key mit ein.  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Dies ist eine Beispielbefehlszeile für die Installation von Visual Studio 2015 Enterprise mit einem MPC von 07060 und dem Product Key "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`  
  
 In der folgenden Tabelle werden die MPC-Codes für jede Edition von Visual Studio aufgelistet:  
  
|Visual Studio-Edition|MPC|  
|---------------------------|---------|  
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
 Weitere Informationen zum Abrufen eines Product Key finden Sie unter [How to: Locate the Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md).  
  
 Wenn der Product Key im Hilfsprogramm „StorePID.exe“ erfolgreich angewendet wurde, wird 0 zurückgegeben. Wenn Fehler gefunden werden, wird eine Zahl zwischen 1 und 6 zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von Visual Studio](../install/install-visual-studio-2015.md)