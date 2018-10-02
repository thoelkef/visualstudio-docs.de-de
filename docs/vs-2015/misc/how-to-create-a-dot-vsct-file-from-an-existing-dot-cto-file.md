---
title: 'Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTO-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: e77ebf34cd56cee80040009cff3ebb2fee9befac
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590597"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTO-Datei
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen binären CTO-Datei erstellen. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen-Compilerformat zu nutzen. Dies funktioniert sogar, wenn die CTO-Datei aus einer CTC-Datei kompiliert wurde. Sie können die VSCT-Datei bearbeiten und in eine andere CTO-Datei kompilieren.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTO-Datei  
  
1.  Erstellen Sie Kopien der CTO-Datei und der zugehörigen .CRSYM-Datei.  
  
2.  Platzieren Sie die Dateien in dem Verzeichnis, in dem sich der Compiler „vsct.exe“ befindet.  
  
3.  Navigieren Sie an der Visual Studio-Eingabeaufforderung zu dem Verzeichnis, das die CTO- und die CTSYM-Datei enthält.  
  
4.  Typ **vsct.exe** _Ctofilename_**CTO** _Vsctfilename_**.vsct-s**  _Symfilename_**.ctsym**.  
  
     `ctofilename` Der Name der CTO-Datei, `vsctfilename` ist der Name der Vsct-Datei, die Sie erstellen möchten, und `symfilename` ist der Name der ctsymdatei.  
  
     Bei diesem Vorgang wird eine neue VSCT-XML-Befehlstabellen-Compilerdatei erstellt. Sie können die Datei mit „vsct.exe“, dem vsct-Compiler, wie jede andere VSCT-Datei bearbeiten und kompilieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen Sie ein. VSCT-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)