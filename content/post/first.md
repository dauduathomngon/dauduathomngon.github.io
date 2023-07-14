---
title: "Test thử xem ổn không"
math: true
comments: true
date: "2023-07-02"
tag: ["test"]
---

## Media testing

{{< youtube 4LPmBiFkoBk >}}

<center>
<img src="https://i.pinimg.com/originals/9f/75/a5/9f75a57a63c19662473771d349da5af3.jpg">
</center>

A cat           |  Another cat
:-------------------------:|:-------------------------:
<img src="https://st3.depositphotos.com/34206678/36588/i/600/depositphotos_365880846-stock-photo-beautiful-cat-fashionable-breed-scottish.jpg"> | <img src="https://st3.depositphotos.com/34206678/36588/i/600/depositphotos_365880846-stock-photo-beautiful-cat-fashionable-breed-scottish.jpg">

## Latex testing
- Inline math: $F(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^{2}}$.
- Display math:
$$
u(n) \Leftrightarrow \frac{1}{{(1 - e^{ - j\omega } )}} + \sum\limits_{k =  - \infty }^\infty  {\pi \delta (\omega  + 2\pi k)}
$$

## Text Testing

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque vitae tellus augue. In orci lectus, tincidunt ut purus sit amet, convallis bibendum enim. Proin lacinia elit suscipit lobortis placerat. Maecenas massa ipsum, hendrerit a feugiat finibus, mollis sed purus. Curabitur sed ipsum ipsum. Maecenas auctor dui nec tellus ullamcorper, nec fermentum risus fringilla. Donec vestibulum porta dictum. Aliquam justo ex, varius non imperdiet vitae, porta quis diam. Vivamus quis tortor ut dui lacinia lobortis sit amet ut turpis. Morbi fringilla risus eget est sodales, in mattis massa sagittis. Morbi vel dignissim dui. Vestibulum ac hendrerit leo. Curabitur pharetra tortor nec est faucibus cursus. Cras et ullamcorper justo, quis dignissim turpis. Fusce condimentum dignissim elit. Aenean efficitur pellentesque elit nec vulputate.

Vivamus sit amet ornare purus, quis feugiat mi. Phasellus mi neque, auctor ut rutrum non, ornare a felis. Praesent convallis elementum quam quis accumsan. Etiam consequat leo augue, eget malesuada ex commodo nec. Curabitur luctus euismod iaculis. Donec sit amet nibh eget risus faucibus sodales. Donec ac sollicitudin tortor. Nunc eleifend diam a nibh ullamcorper, vel dignissim ante porttitor. Aenean posuere ut tortor vel congue.

In a justo sit amet orci consectetur eleifend. Proin nec est varius, tincidunt enim et, accumsan quam. Curabitur nec porttitor ex. Duis luctus felis a nunc laoreet, et convallis ante tristique. Vestibulum erat nisi, tincidunt vel leo vel, vestibulum sagittis enim. Nam nibh odio, eleifend et efficitur non, ornare ut est. Aenean at justo eget ligula sodales mattis. Praesent congue sapien eu rhoncus bibendum. Integer vel euismod erat, at varius est. Fusce mi eros, lobortis quis ullamcorper et, tempor et elit. Fusce sed pulvinar tellus. Etiam arcu quam, scelerisque sit amet eros id, lacinia eleifend nunc. Aenean vel tortor nec dolor tincidunt convallis ut vel ante. Nulla ligula eros, ullamcorper quis nisl at, lacinia hendrerit ipsum. Donec venenatis diam in ante sagittis vehicula. Donec ultrices maximus odio at sollicitudin.

Donec ornare mi vitae tristique cursus. Integer sed sagittis tortor, sed facilisis quam. Suspendisse potenti. Suspendisse tincidunt condimentum mi a sagittis. Sed feugiat accumsan dui, nec elementum augue gravida at. Sed at tincidunt velit. Nunc ipsum enim, iaculis ac rhoncus et, faucibus vitae felis. Aliquam erat volutpat. Nunc pretium pharetra tortor ac mattis.

Aenean enim metus, pellentesque sed purus in, rhoncus dictum nisl. Vivamus ultrices lectus tortor, in semper augue faucibus eget. In ac lacinia nunc, et tempor sapien. Aliquam rhoncus purus ut facilisis sollicitudin. Aliquam hendrerit tempor sagittis. Phasellus eget leo tincidunt, dignissim dui eget, dapibus magna. Donec id pretium nibh. Praesent vestibulum luctus nisl sed elementum. Duis vel lorem arcu. Fusce placerat a turpis non luctus. Duis a sagittis leo, at eleifend lorem.

## Code testing

```cpp
#include <SDL2/SDL.h>
#include <cstdlib>
#include <iostream>

int main()
{
    using std::cerr;
    using std::endl;

    if (SDL_Init(SDL_INIT_EVERYTHING) != 0) {
        cerr << "SDL_Init Error: " << SDL_GetError() << endl;
        return EXIT_FAILURE;
    }

    SDL_Window* win = SDL_CreateWindow("Hello World!", 100, 100, 620, 387, SDL_WINDOW_SHOWN);
    if (win == nullptr) {
        cerr << "SDL_CreateWindow Error: " << SDL_GetError() << endl;
        return EXIT_FAILURE;
    }

    SDL_Renderer* ren
        = SDL_CreateRenderer(win, -1, SDL_RENDERER_ACCELERATED | SDL_RENDERER_PRESENTVSYNC);
    if (ren == nullptr) {
        cerr << "SDL_CreateRenderer Error" << SDL_GetError() << endl;
        SDL_DestroyWindow(win);
        SDL_Quit();
        return EXIT_FAILURE;
    }

    SDL_Surface* bmp = SDL_LoadBMP("../img/grumpy-cat.bmp");
    if (bmp == nullptr) {
        cerr << "SDL_LoadBMP Error: " << SDL_GetError() << endl;
        SDL_DestroyRenderer(ren);
        SDL_DestroyWindow(win);
        SDL_Quit();
        return EXIT_FAILURE;
    }

    SDL_Texture* tex = SDL_CreateTextureFromSurface(ren, bmp);
    if (tex == nullptr) {
        cerr << "SDL_CreateTextureFromSurface Error: " << SDL_GetError() << endl;
        SDL_FreeSurface(bmp);
        SDL_DestroyRenderer(ren);
        SDL_DestroyWindow(win);
        SDL_Quit();
        return EXIT_FAILURE;
    }
    SDL_FreeSurface(bmp);

    for (int i = 0; i < 20; i++) {
        SDL_RenderClear(ren);
        SDL_RenderCopy(ren, tex, nullptr, nullptr);
        SDL_RenderPresent(ren);
        SDL_Delay(100);
    }

    SDL_DestroyTexture(tex);
    SDL_DestroyRenderer(ren);
    SDL_DestroyWindow(win);
    SDL_Quit();

    return EXIT_SUCCESS;
}
```
