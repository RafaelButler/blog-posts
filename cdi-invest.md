<div className="flex flex-col md:flex-row" style="gap: 1rem;">
  <div className="w-full md:mr-4">
    <img
      className="mr-4 my-2 w-[200px] rounded-lg"
      alt="infos"
      height="200px"
      src="/investidor-plataform/desktop.png"
    />
  </div>
  <div className="flex justify-start space-x-20  w-full" style="gap: 1rem;">
    <img
      className="mr-4 w-[50px] my-2"
      alt="infos"
      height="50px"
      width="100px"
      src="/investidor-plataform/infos.jpg"
    />
    <img
      className="mr-4 w-[50px] my-2"
      alt="infos"
      height="50px"
      width="100px"
      src="/investidor-plataform/grafico.jpg"
    />
  </div>
</div>

## How the CDI works

- [Investidor CDI](https://invistacdi.vercel.app/)

The CDI (Interbank Deposit Certificate) is a very short-term security issued by banks. It is a very popular investment, and at the time of writing this article, its rates are very favorable.

Thinking about helping to answer questions about returns, I decided to create a [website](https://invistacdi.vercel.app/) to simulate the returns linked to the CDI.

One of the things that few people consider, but which is **crucial**, is the effect of inflation on returns over time.

You can simulate your initial contribution and monthly contributions, and see the return over time on the effect of inflation.

The values ​​are updated automatically according to the Brazil Central Bank.

## What was used?

- React.js
- Next.js 14
- Server components concepts
- Shadcn/ui
- Prisma