# Bot que responde

''' language "python"
    import os
from telegram import Bot
from telegram.ext import MessageHandler, Filters, Updater

# Configura tu token de bot
TOKEN = "tu_token_aqui"

# Directorio donde se guardarán las fotos
SAVE_DIR = "fotos_descargadas"

if not os.path.exists(SAVE_DIR):
    os.makedirs(SAVE_DIR)

def download_photo(update, context):
    message = update.message
    if message.photo:
        # Descargar la foto
        file_id = message.photo[-1].file_id
        file = context.bot.get_file(file_id)
        file.download(os.path.join(SAVE_DIR, f"{file_id}.jpg"))

def main():
    bot = Bot(token=TOKEN)
    updater = Updater(bot=bot, use_context=True)
    dp = updater.dispatcher

    dp.add_handler(MessageHandler(Filters.photo, download_photo))

    # Iniciar el bot
    updater.start_polling()
    updater.idle()

if __name__ == '__main__':
    main()
'''

... y ya está!!