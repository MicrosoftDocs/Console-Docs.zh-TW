---
title: 清除畫面
description: 如何使用系統功能或以程式設計方式使用公用 API 函式來清除 Windows 主控台的畫面。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_clearing\_the\_screen'
- base.clearing\_the\_screen
- consoles.clearing\_the\_screen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2097cc53-13b9-4f29-9d2c-feea56a27cb8
ms.openlocfilehash: fd2a407e56d6b0fe00db59c5f783cb13546119f6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059370"
---
# <a name="clearing-the-screen"></a>清除畫面


有兩種方式可以清除主控台應用程式中的畫面。

## <a name="span-idexample_1spanspan-idexample_1spanspan-idexample_1spanexample-1"></a><span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>範例1


第一個方法是使用 C 執行時間 **系統** 函數。 **系統**函式會叫用命令直譯器所提供的**cls**命令以清除畫面。

```C
#include <stdlib.h>

int main( void )
{
    system("cls");
    return 0;
}
```

## <a name="span-idexample_2spanspan-idexample_2spanspan-idexample_2spanexample-2"></a><span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>範例2


第二種方法是撰寫函式，以程式設計方式使用 [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) 和 [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) 函數來清除畫面。 下列範例程式碼示範這項技術。

```C
#include <windows.h>

void cls( HANDLE hConsole )
{
   COORD coordScreen = { 0, 0 };    // home for the cursor 
   DWORD cCharsWritten;
   CONSOLE_SCREEN_BUFFER_INFO csbi; 
   DWORD dwConSize;

// Get the number of character cells in the current buffer. 

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   dwConSize = csbi.dwSize.X * csbi.dwSize.Y;

   // Fill the entire screen with blanks.

   if( !FillConsoleOutputCharacter( hConsole,        // Handle to console screen buffer 
                                    (TCHAR) ' ',     // Character to write to the buffer
                                    dwConSize,       // Number of cells to write 
                                    coordScreen,     // Coordinates of first cell 
                                    &cCharsWritten ))// Receive number of characters written
   {
      return;
   }

   // Get the current text attribute.

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   // Set the buffer's attributes accordingly.

   if( !FillConsoleOutputAttribute( hConsole,         // Handle to console screen buffer 
                                    csbi.wAttributes, // Character attributes to use
                                    dwConSize,        // Number of cells to set attribute 
                                    coordScreen,      // Coordinates of first cell 
                                    &cCharsWritten )) // Receive number of characters written
   {
      return;
   }

   // Put the cursor at its home coordinates.

   SetConsoleCursorPosition( hConsole, coordScreen );
}

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);
    
    return 0;
}
```

 

 




