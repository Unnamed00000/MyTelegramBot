# MyTelegramBot
Привет! 👋 Я твой личный бот. Отвечаю тем, кто тебе пишет. 
from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

# my_bot.py
TOKEN = '7036290270:AAFkmMaFL9oW_aIMgNyhcHvqj2Y0W9zBqVQ'

def start(update: Update, context: CallbackContext) -> None:
    update.message.reply_text('Привет! Я ваш бот. Жду ваши сообщения.')

def handle_messages(update: Update, context: CallbackContext) -> None:
    # Отвечаем на любое полученное сообщение
    update.message.reply_text('Спасибо за ваше сообщение! Мой хозяин скоро ответит.')

def main() -> None:
    updater = Updater(TOKEN)
    dp = updater.dispatcher

    # Добавляем обработчик команды /start
    dp.add_handler(CommandHandler("start", start))

    # Добавляем обработчик всех входящих сообщений
    dp.add_handler(MessageHandler(Filters.text & ~Filters.command, handle_messages))

    # Запускаем бота
    updater.start_polling()

    # Запускаем бота и ожидаем завершения
    updater.idle()

if __name__ == '__main__':
    main()
