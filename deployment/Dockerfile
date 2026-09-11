FROM python:3.9

# Set up a non-root user for Hugging Face Spaces
RUN useradd -m -u 1000 user
USER user
ENV HOME=/home/user \
    PATH=/home/user/.local/bin:$PATH

WORKDIR $HOME/app

# Copy requirements and install
COPY --chown=user requirements.txt $HOME/app/requirements.txt
RUN pip install --no-cache-dir --user --upgrade -r requirements.txt

# Copy the rest of the application
COPY --chown=user . $HOME/app

# Expose port 7860 for Hugging Face Spaces
EXPOSE 7860

# Use ENTRYPOINT to ensure streamlit is the primary process
ENTRYPOINT ["streamlit", "run", "app.py", "--server.port", "7860", "--server.address", "0.0.0.0"]
