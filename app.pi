from fastapi import FastAPI, Request
import requests
import os

app = FastAPI()
TOKEN = os.getenv("TELEGRAM_TOKEN")
URL = f"https://api.telegram.org/bot{TOKEN}/sendMessage"

@app.post("/webhook")
async def webhook(req: Request):
    data = await req.json()
    chat_id = data["message"]["chat"]["id"]
    text = data["message"]["text"]
    requests.post(URL, json={"chat_id": chat_id, "text": f"Echo: {text}"})
    return {"ok": True}
