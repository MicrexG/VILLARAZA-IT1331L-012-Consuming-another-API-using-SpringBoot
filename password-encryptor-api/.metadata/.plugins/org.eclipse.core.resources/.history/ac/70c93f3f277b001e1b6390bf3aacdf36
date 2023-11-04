package com.uap.it1311l.passwordencryptorapi.service;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import com.uap.it1311l.passwordencryptorapi.models.EncryptionResponse;
import com.uap.it1311l.passwordencryptorapi.webclient.EncryptionApiClient;
import com.uap.it1311l.passwordencryptorapi.webclient.EncryptionMyBatisMapper;

@Service
public class EncryptDecryptService {
	@Autowired
	EncryptionApiClient apiClient;
	
	@Autowired
	EncryptionMyBatisMapper mybatisMapper;
	
	public EncryptionResponse encrypt(String password) {
		EncryptionResponse alligator = apiClient.encrypt("getpass", password, "AES");
		mybatisMapper.insert(alligator.getResult());
		return alligator;
	}
	
	public String decrypt(String hash) {
		if (mybatisMapper.exists(hash) > 0) {
			EncryptionResponse alligator = apiClient.decrypt("getpass", hash, "AES");
			return alligator.getResult();
		} else {
			return "Encrypted Password does not exist.";
		}
	}
}
