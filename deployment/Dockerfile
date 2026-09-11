FROM python:3.9

# Set up a non-root user for Hugging Face Spaces
RUN useradd -m -u 1000 user
USER user
ENV HOME=/home/user \
    PATH=/home/user/.local/bin:$PATH

WORKDIR $HOME/app

# Copy requirements and install
# Using --user to ensure permissions match the non-root user
COPY --chown=user requirements.txt $HOME/app/requirements.txt
RUN pip install --no-cache-dir --user --upgrade -r requirements.txt

# Copy the rest of the application
COPY --chown=user . $HOME/app

# Expose port 7860 for Hugging Face Spaces
EXPOSE 7860

# Command to run the app
CMD ["streamlit", "run", "app.py", "--server.port", "7860", "--server.address", "0.0.0.0"]
