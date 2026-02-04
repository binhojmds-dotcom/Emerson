# Emerson
Loja
import { useState } from "react";
import { ShoppingCart, MessageCircle } from "lucide-react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function ModasFamas() {
  const [cart, setCart] = useState([]);

  const produtos = [
    { id: 1, nome: "Camiseta Grife Premium", preco: 199.9 },
    { id: 2, nome: "Calça Jeans Grife", preco: 349.9 },
    { id: 3, nome: "Moletom Exclusivo", preco: 499.9 },
  ];

  function addCarrinho(produto) {
    setCart([...cart, produto]);
  }

  const total = cart.reduce((s, p) => s + p.preco, 0);

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <header className="flex justify-between items-center mb-8">
        <h1 className="text-3xl font-bold">Modas Famas</h1>
        <div className="flex items-center gap-3">
          <ShoppingCart /> {cart.length}
        </div>
      </header>

      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {produtos.map((p) => (
          <Card key={p.id} className="rounded-2xl">
            <CardContent className="p-5 text-center">
              <div className="h-40 bg-gray-200 rounded-xl mb-4"></div>
              <h2 className="text-xl font-semibold">{p.nome}</h2>
              <p className="text-green-600 font-bold mt-2">
                R$ {p.preco.toFixed(2)}
              </p>
              <Button className="mt-4 w-full" onClick={() => addCarrinho(p)}>
                Adicionar ao carrinho
              </Button>
            </CardContent>
          </Card>
        ))}
      </div>

      <div className="mt-10 bg-white rounded-2xl p-5 shadow">
        <h2 className="text-xl font-bold mb-2">Carrinho</h2>
        {cart.map((p, i) => (
          <p key={i}>{p.nome}</p>
        ))}
        <p className="font-bold mt-2">Total: R$ {total.toFixed(2)}</p>

        <a
          href={`https://wa.me/5511915296760?text=Quero%20comprar%20na%20Modas%20Famas%20-%20Total%20R$%20${total.toFixed(2)}`}
          target="_blank"
        >
          <Button className="mt-4 w-full flex gap-2">
            <MessageCircle /> Comprar pelo WhatsApp
          </Button>
        </a>
      </div>

      <footer className="text-center text-gray-500 mt-10">
        © 2026 - Modas Famas · modasfamas.com · Vendas via WhatsApp, Pix e Cartão
      </footer>
    </div>
  );
}
