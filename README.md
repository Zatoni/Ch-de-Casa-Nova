import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { useState } from "react";

export default function ChaDeCasaNova() {
  const [nome, setNome] = useState("");
  const [presente, setPresente] = useState("");
  const [mensagem, setMensagem] = useState("");
  const [confirmado, setConfirmado] = useState(false);

  const handleSubmit = (e) => {
    e.preventDefault();
    setConfirmado(true);
  };

  return (
    <div className="p-4 max-w-4xl mx-auto space-y-6">
      <h1 className="text-4xl font-bold text-center">Chá de Casa Nova</h1>
      <h2 className="text-xl text-center text-gray-600">Monique e Guilherme - 21/06/2025</h2>

      <Card>
        <CardContent className="p-6 space-y-4">
          <h3 className="text-2xl font-semibold">Lista de Presentes</h3>
          <ul className="list-disc list-inside space-y-1">
            <li>Jogo de talheres</li>
            <li>Jogo de pratos</li>
            <li>Conjunto de copos e taças</li>
            <li>Jogo de panelas</li>
            <li>Assadeiras e utensílios</li>
            <li>Liquidificador, batedeira, air fryer</li>
            <li>Micro-ondas, cafeteira</li>
            <li>Geladeira 450L</li>
            <li>Máquina de lavar roupas</li>
            <li>Jogo de cama e banho</li>
            <li>Itens de limpeza e decoração</li>
          </ul>
        </CardContent>
      </Card>

      <Card>
        <CardContent className="p-6 space-y-4">
          <h3 className="text-2xl font-semibold">Confirme seu presente 🎁</h3>
          {confirmado ? (
            <p className="text-green-600 font-medium">Obrigado! Presente confirmado 💖</p>
          ) : (
            <form onSubmit={handleSubmit} className="space-y-4">
              <Input
                placeholder="Seu nome"
                value={nome}
                onChange={(e) => setNome(e.target.value)}
                required
              />
              <Input
                placeholder="Presente escolhido"
                value={presente}
                onChange={(e) => setPresente(e.target.value)}
                required
              />
              <Textarea
                placeholder="Mensagem para o casal (opcional)"
                value={mensagem}
                onChange={(e) => setMensagem(e.target.value)}
              />
              <Button type="submit">Confirmar Presente</Button>
            </form>
          )}
        </CardContent>
      </Card>

      <div className="text-center text-sm text-gray-500">
        Local do chá e mais informações serão enviados por WhatsApp 💌
      </div>
    </div>
  );
}
